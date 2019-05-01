# Further Many-to-Many Patterns

There are a few other common DB patterns that rails allows with different model association keywords.


### Has Many Through
If you have a join-like table that ALSO has extra data or needs its own model, you can use `has_many_through` to hook those models up.

(Taken directly from the rails [docs](https://guides.rubyonrails.org/v5.2/association_basics.html#the-has-many-through-association))


```ruby
class Physician < ApplicationRecord
  has_many :appointments
  has_many :patients, through: :appointments
end

class Appointment < ApplicationRecord
  belongs_to :physician
  belongs_to :patient
end

class Patient < ApplicationRecord
  has_many :appointments
  has_many :physicians, through: :appointments
end
```

```ruby
class CreateAppointments < ActiveRecord::Migration[5.2]
  def change
    create_table :physicians do |t|
      t.string :name
      t.timestamps
    end

    create_table :patients do |t|
      t.string :name
      t.timestamps
    end

    create_table :appointments do |t|
      t.belongs_to :physician
      t.belongs_to :patient
      t.datetime :appointment_date
      t.timestamps
    end
  end
end
```

### Self-Referencing Foreign Key
If you have a join table where more than one column in the join table references the same primary key column in the same table, you can name the foreign keys.

Note that getting the correct behavior in active record requires 2 sets of references in the model.

From: (https://medium.com/@esmerycornielle/making-a-followers-feature-with-ruby-on-rails-and-active-record-ddb3d1dda060)[https://medium.com/@esmerycornielle/making-a-followers-feature-with-ruby-on-rails-and-active-record-ddb3d1dda060]


##### Following

```ruby
create_table :users do |t|
  t.string :name
  t.timestamps
end

create_table :follows do |t|
  t.integer :user_id
  t.integer :following_id
  t.timestamps
end
```

```ruby
class Follow < ActiveRecord::Base
  belongs_to :follower, foreign_key: :user_id, class_name: 'User'
  belongs_to :following, foreign_key: :following_id, class_name: 'User'
end
```

```ruby
class User < ActiveRecord::Base
  has_many :follows

  # link the following_id column in Follow class to this "virtual table"

  has_many :follower_relationships, foreign_key: :following_id, class_name: 'Follow'

  # user follower_relationships in the has_many
  # has_many gives us some_user.follower
  # source follower refers to the belongs_to in the user model

  has_many :followers, through: :follower_relationships, source: :follower

  # link the user_id column in Follow class to this "virtual table"

  has_many :following_relationships, foreign_key: :user_id, class_name: 'Follow'

  # user following_relationships in the has_many
  # has_many gives us some_user.following
  # source following refers to the belongs_to in the user model
  has_many :following, through: :follower_relationships, source: :following
end
```

```ruby

chee_kean = User.new(name: "Chee Kean")

chee_kean.save

susan_chan = User.new(name: "Susan Chan")

susan_chan.save

chee_kean.followers << susan_chan
```


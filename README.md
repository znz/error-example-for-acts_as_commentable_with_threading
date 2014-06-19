# error example for acts_as_commentable_with_threading

## versions

- `ruby` 2.1.2
- `rails` 4.1.1
- `acts_as_commentable_with_threading` 1.2.0
- `awesome_nested_set` 3.0.0.rc.5

## problem

`belongs_to` with `:touch => true` in `Comment`,
and `comment.save` raises error in `touch_record`.

## how to re-produce

    % rake db:seed
    [:touch_record, #<Comment id: 1, commentable_id: 1, commentable_type: "Post", title: nil, body: "debug", subject: nil, user_id: 1, parent_id: nil, lft: 1, rgt: 2, created_at: "2014-06-19 10:46:10", updated_at: "2014-06-19 10:46:10">, "commentable_id", :commentable, true]
    {"commentable_id"=>0, "commentable_type"=>nil, "user_id"=>0, "body"=>nil, "created_at"=>nil, "updated_at"=>nil, "lft"=>nil, "rgt"=>nil, "id"=>nil}
    [#<Comment id: 1, commentable_id: 1, commentable_type: "Post", title: nil, body: "debug", subject: nil, user_id: 1, parent_id: nil, lft: 1, rgt: 2, created_at: "2014-06-19 10:46:10", updated_at: "2014-06-19 10:46:10">, "Post", nil]
    rake aborted!
    NoMethodError: undefined method `constantize' for nil:NilClass
    /private/tmp/error-example-for-acts_as_commentable_with_threading/config/initializers/belongs_to.rb:14:in `touch_record'
    /private/tmp/error-example-for-acts_as_commentable_with_threading/db/seeds.rb:13:in `<top (required)>'
    Tasks: TOP => db:seed
    (See full trace by running task with --trace)

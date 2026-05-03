```Plain Text
// Use DBML to define your database structure
// Docs: https://dbml.dbdiagram.io/docs

Table users {
  uid integer [primary key]
  nick string [not null, unique]
  email string [not null, unique]
  password string [not null]
  image_url string
}

Table users_streak {
  uid integer [primary key]
  activity_date date [primary key]
}

Table tasks {
  id integer [primary key]
  order_id integer [not null]
  title string [not null]
  answer string [not null]
  image_url string
}

Table stat_per_task {
  uid integer [primary key]
  order_id integer [primary key]
  wrong_decision_count integer
  right_decision_count integer
}

Table task_orders {
  id integer [primary key]
  number integer [unique]
}

Ref: "users"."uid" < "stat_per_task"."uid"

Ref: "users"."uid" < "users_streak"."uid"

Ref: "task_orders"."id" < "stat_per_task"."order_id"

Ref: "task_orders"."id" < "tasks"."order_id"
```
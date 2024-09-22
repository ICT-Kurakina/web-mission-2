# Mission 2

## Part 1
[https://drive.google.com/file/d/179zhRsN3XCF0Z3JLfjyTTid1jN0MfRGk/view?usp=sharing](https://drive.google.com/file/d/179zhRsN3XCF0Z3JLfjyTTid1jN0MfRGk/view?usp=sharing)

## Part2

###*1.Получить список юзернеймов пользователей*
  select username from users

###*2.Получить кол-во отправленных сообщений каждым пользователем*
  select users.username, count (messages. id) as number_of_sent_messages from users
  left join messages on users.id = messages.from
  group by users.id

###*3.Получить пользователя с самым большим кол-вом полученных сообщений и само количество*
  select users.username, count(messages.id) as received_messages from users
  join messages on users.id = messages.to
  group by users.id
  order by received _messages desc
  limit 1

###*4.Получить среднее кол-во сообщений, отправленное каждым пользователем*
  select avg (number_of_sent_messages) as avg_number_of_sent_messages 
  from (
    select count (messages.id) as number_of_sent_messages 
    from users
    left join messages on users. id = messages.from
    group by users. id 
  ) as count_for_users

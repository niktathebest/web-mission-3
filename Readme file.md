# Mission 3

## Videos

[Supabase](https://disk.yandex.ru/i/unIcvFkm7U4dwQ)
[Buildship 1](https://disk.yandex.ru/i/aW5iS22sHXkNUA)
[Buildship 1](https://disk.yandex.ru/i/--njhxeA6T5s_Q)

## Part1

- Получить список юзернеймов пользователей 
> SELECT username
FROM users;

- Получить кол-во отправленных сообщений каждым пользователем:
    username - number of sent messages	 
> SELECT u.username, COUNT(m.id) AS number_of_sent_messages
FROM users u
LEFT JOIN messages m ON u.id = m.from
GROUP BY u.username; 

- Получить пользователя с самым большим кол-вом полученных сообщений и само количество  
    username - number of received messages 
> SELECT u.username, COUNT(m.id) AS number_of_received_messages
FROM users u
LEFT JOIN messages m ON u.id = m.to
GROUP BY u.username
ORDER BY number_of_received_messages DESC
LIMIT 1; 

- Получить среднее кол-во сообщений, отправленное каждым пользователем
> SELECT AVG(sent_messages) AS average_sent_messages
FROM (
    SELECT COUNT(m.id) AS sent_messages
    FROM users u
    LEFT JOIN messages m ON u.id = m.from
    GROUP BY u.id
) AS message_counts;  

Зачем?

Например есть система достижений и есть достижение за просмотр поста
два человека одновременно посещают один пост идут два ивента на повышение ачивмент прогресса на 1

происходит считывание ачивмент прогресса - увеличение на 1 - запись в бд

но если нет лока, то 1 изменение перетрется, поэтому надо ставить лок на выбор ачивмент прогресса для конкретного пользователя по конкретному ачивменту
[[Optimistic Locking]]
[[Pessimistic Locking]]

----------------
сейчас сомнительно, [[Atomic update or delete]]

----------------------

допустим в одной операции делаем select в другой операции update или insert этих данных, так как read committed то данные могут поменяться, поэтому надо делать select for update или оптимистик лок, чтобы залочить запись, чтоб она никем не изменилась
#бд 
#postgresql
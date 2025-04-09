BEGIN;
SELECT balance FROM accounts
WHERE user_id = 1 FOR UPDATE;

UPDATE accounts SET balance = 200
WHERE user_id = 1;
COMMIT;

при этом в двух параллельных транзакциях можно делать select for update, просто последняя транзакция завершится с ошибкой

блокирует строку - реализация [[Pessimistic Locking]]

#бд 
#postgresql
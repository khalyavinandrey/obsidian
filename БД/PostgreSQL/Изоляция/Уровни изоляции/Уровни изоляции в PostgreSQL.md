каждая транзакция работает с согласованным снимком данных на определенный момент времени, в снимок попадают все изменения, зафиксированные до момента его создания

таким образом реализация изоляции с помощью снимков позволяет обходиться минимумом блокировок
блокируется лишь повторное изменение строки
при этом изменение строки не блокирует чтение строки
и чтение строки вообще никого не блокирует

[[Read committed]]
[[Repeatable read]]
[[Serializable]]

#бд 
#postgresql 

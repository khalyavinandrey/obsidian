сократить количество обращений к бд
ускорить дорогие запросы

надо чтобы eviction policy совпадал у каждой ноды кэша
имнвалидация кэша

cache write strategy - проблема с обеспечением констистентности в кэше и бд:
одновременная запись в кэш и бд (slower for write ops)
запись в бд (increase data fetch times on subsequent reads)
запись в кэш и асинхронно в бд (data loss if cache is not persisted to disk)

#systemdesign
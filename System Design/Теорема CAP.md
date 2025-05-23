Согласно теореме CAP распределенная система может обеспечивать не более двух из трех свойств:

- Consistency - пользователь будет получать одинаковую информацию с любого узла системы
- Availability - при выходе одного из узлов - система продолжит функционировать и пользователь будет получать данные, правда эти данные могут быть устаревшими
- Partition Tolerance - вопреки нарушению связи в сети между некоторыми узлами в системе, пользователь продолжит получать данные

В распределенных системах всегда поддерживается Partition Tolerance, потому что в любых распределенных системах проблемы с сетью - неизбежны

Поэтому в зависимости от требований к системе, системы делятся по свойствам на CP и AP

Пример идеальной ситуации: Все записи происходят через реплику a1 и данные копируются на реплики a2 и a3, пользователь получает актуальную информацию с любой ноды - пример CP

Пример реальной ситуации: реплика a3 теряет связь с репликами a1 и a2, если консистентность данных некритична и будет не критично, если пользователь получит неактуальные данные с ноды a1 или a2 - то подойдет система AP, если же важно, чтобы на пользователь с любого узла получал одинаковую информацию, то нужно заблокировать запись в a1 и a2, чтобы обеспечить избежание рассинхронизации данных и соответственно это приведет к недоступности системы, такое критично для банков - CP система
#systemdesign
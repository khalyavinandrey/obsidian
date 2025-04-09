API:
- create(file)
- delete(file)
- copy(d, s)
- pread(f, offset, sizeByte)
- write(p, o, data) - не нравится
- append(p, data)
отсылка к [[Файловые системы]]
![[Pasted image 20240818182111.png]]

Read -> meta store -дай список чанков такого размера> получаем список чанков -> chunk store -> читаем чанки
append -> chunk store -запиши метаданные> получаем идентификатор чанка -идем в meta store > ms.Append(file, id чанка)
copy - скопировать Inode с чанками
![[Pasted image 20240818184903.png]]


![[Pasted image 20240818185302.png]]

запрос put(d) принимает мастер chunk стора и направляет запросы на 3 ноды: на 2 ноды синхронно, на одну асинхронно 


### netology-os-1

1. chdir("/tmp")  

2. в /usr/bin/file

3. выполняем `lsof | grep delete` → в выводе ищем нужный нам удалённый файл и ИД процесса, использующего его и номер дескриптора → убиваем процесс → приводим размер файла к нолю используя truncate или `> /proc/[process_id"X"]/fd/[fd_num"Y"]`  
   

4. Зомби процессы не занимают ресурсов, но занимают имеющий ограничения пул доступных процессов  
  
5. `strace -e trace=openat file opensnoop-bpfcc`  
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3  
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libmagic.so.1", O_RDONLY|O_CLOEXEC) = 3  
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3  
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/liblzma.so.5", O_RDONLY|O_CLOEXEC) = 3  
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libbz2.so.1.0", O_RDONLY|O_CLOEXEC) = 3  
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libz.so.1", O_RDONLY|O_CLOEXEC) = 3  
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libpthread.so.0", O_RDONLY|O_CLOEXEC) = 3  
openat(AT_FDCWD, "/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = 3  
openat(AT_FDCWD, "/etc/magic.mgc", O_RDONLY) = -1 ENOENT (No such file or directory)  
openat(AT_FDCWD, "/etc/magic", O_RDONLY) = 3  
openat(AT_FDCWD, "/usr/share/misc/magic.mgc", O_RDONLY) = 3  
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache", O_RDONLY) = 3  
openat(AT_FDCWD, "opensnoop-bpfcc", O_RDONLY|O_NONBLOCK) = -1 ENOENT (No such file or directory)  
opensnoop-bpfcc: cannot open `opensnoop-bpfcc' (No such file or directory)  

6.ff  

7. При `;` выполняется вторая команда вне зависимости от результата первой, а при `&&` вторая команда выполнится только при успехе первой.  
  `set -e` прекращает выполнение скрипта, если команда завершилась с ошибкой, делает вывод в stderr. Так же для отдельной команды в конвеере можно отключить эту проверку. В некоторых ситуациях можно использовать этот функционал.   
  

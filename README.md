# Linux
# Конспект по курсу LPIC 105.2.

## Linux. Конспект по курсу LPIC 105.2.

## Часть 1. Создание простого bash скрипта.
Итак. 
Bash Скрипт - это скрипт, который исполняется системой линукс. на конце может быть расширение .sh
Любой bash скрипт должен начинаться с символов Shibang -то есть #!
После данного символа обозначается какой интерпретатор, то есть исполнитель языка будет использоваться например:
```bash
#!/bin/bash
```
Также есть основные элементы bash скрипта:
```bash
# ///коментарий строки, то есть можно написать так:
#комментарий строки
chown ///смена владельца файла. Посмотреть все возможные комбинации chown можно:
chown --help
chmod /// назначение прав, смена прав доступа. Посмотреть все возможные комбинации chmod можно:
chmod --help
SUID ///бит запуска от имени владельца
```
И опять пример простейшего Bash скрипта:
```bash
file /home/linux/script.sh
___________________
#!/bin/bash
#Question script
echo 'Are you hungry? ' ///задаем вопрос
read VALUE ///чтение переменной с клавиатуры
if [ $VALUE = "YES" ]; ///Сравниваем условие
then ///тогда
echo 'Make some dinner' ///Действие если да
else
echo 'Continue working' ///Действие если нет
fi ///Обозначаем конец скрипта.
```
И когда мы запустим этот скрипт, он спросит хотим ли мы есть и если мы ответим да, то он напишет: приготовь что-то поесть(по-английски), а если мы ответим нет, то напишет : Продолжай работать.
Чтобы все пользователи могли запустить срипт с правами владельца, нужно установить SUID бит командой 
```bash
chmod u+s /home/linux/script.sh ///установим SUID бит
```
Когда мы установим SUID бит, наш скрипт при команде ls -l станет красным и значит мы все сделали правильно.

## Часть 2. Программа test
У команды test есть несколько опций:
```bash
test [OPTIONS] [file]
Options:
+x - исполняемый файл
-e - файл существует
-eq - значения равны
-ne - значения не равны
-z - существует ли значение
///На выходе дает переменной $?:
///0 если результат положительный
/// не 0 если результат отрицательный
```
Примеры команды test:
```bash
///Проверить больше ли первое число второго
test 5 -gt 2
echo $?
```
или
```bash
[ 5 -gt 2 ]
echo ?
```

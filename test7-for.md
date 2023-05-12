# Command's Format

for task in <tasks list>
do
  command $task
done

# From file

## From file v1
all-tasks.txt

for task in `cat all-tasks.txt`
do
  command $task
done


## From file v2 (Best Practise)

for task in $(cat all-tasks.txt)
do
  command $task
done


# Sequence

## Sequence v1 

for task in {0..15}
do
  command task-num-$task
done


## Sequence v2

for (( task=0 ; task <= 15 ; task++ ))
do
  command task-num-$task
done


## Sequence Example1

for file in $(ls)
do
  echo File $file has $(cat $file | wc -l)
done


## Sequence Example2

for package in $(cat packages-to-install.txt)
do
  sudo apt-get -y install $package
done


## Sequence Example3

for server in $(cat server-list.txt)
do
  ssh $server "uptime"
done


## Sequence Example4

Скрипт должен получать название директории, найти ее в домашней директории пользователя, а в ней сделать все sh-файлы исполняемыми. В нем какая-то ошибка, попробуй исправить.

Мы создали директорию /home/moon/scripts. В нем несколько скриптов, попробуй запустить /home/moon/add-exec-to-directory.sh scripts.


if [ $# -eq 0 ] 
then
  echo 'No argument'
  exit
fi

directory=$1

for file in $HOME/$directory/*.sh; do
  chmod +x "${file}"
done



## Sequence Example5

У нас есть несколько различных приложений, работающих в этой системе. Список приложений хранится в файле apps.txt. Логи каждого из этих приложений хранятся в каталоге /var/log/apps в файле с его названием. Проверь это!



Разработана простая версия скрипта /home/moon/count-requests.sh, которая проверяет лог-файл приложения и печатает количество запросов типа GET, POST, PATCH, HEAD, PUT и DELETE. Обнови скрипт для использования цикла for, чтобы вычитывать список приложений из файла /home/moon/apps.txt с подсчета количества запросов для каждого приложения. Вывод осуществляется в формате таблицы:

Log name GET POST PATCH HEAD PUT DELETE

- - - - - - - - - - - - - - - - - - - - - - - - - - -

manager 17 16 20 15 13 13

ci-runners 13 6 14 11 5 10




for app in $(cat /home/moon/apps.txt)
do

cd /var/log/apps/

echo -e " Log name \tGET \tPOST \tPATCH \tHEAD \tPUT \tDELETE "
echo -e "---------------------------------------------------------------"

get_requests=$(cat ${app}_app.log | grep "GET" | wc -l)
post_requests=$(cat ${app}_app.log | grep "POST" | wc -l)
patch_requests=$(cat ${app}_app.log | grep "PATCH" | wc -l)
head_requests=$(cat ${app}_app.log | grep "HEAD" | wc -l)
put_requests=$(cat ${app}_app.log | grep "PUT" | wc -l)
delete_requests=$(cat ${app}_app.log | grep "DELETE" | wc -l)

echo -e " $app \t${get_requests} \t${post_requests} \t${patch_requests} \t ${head_requests} \t${put_requests} \t${delete_requests}"
done



## Sequence Example6

переименовать все файлы внутри папки texts у которых расширение txt в md. Файлы с любым другим расширением должны остаться прежними.


for name in $(ls /home/moon/texts)
do
  if [[ $name = *".txt"* ]]
  then
    new_name=$(echo $name | sed 's/.txt/.md/g')
    mv texts/name texts/$new_name
  fi
done
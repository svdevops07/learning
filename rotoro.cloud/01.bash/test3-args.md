task_name=$1

mkdir dir_$1
echo $1
start-command with $task_name


# Best Practice

task_name is CORECT
task-name is INCORECT
task_name != TASK_NAME


task_name is GOOD
TaskName / Task_Name is BAD

log_path="/var/log/${service}_daily/log.txt"


# Этот скрипт создает бэкап данного файла, создавая копию как <filename>_bu
# Например 'my-pic.jpg' будет забэкаплен как 'my-pic.jpg_bu'
set -e

file_name=$1

cp $file_name ${file_name}_bu

echo "Done!"




--------------------
У нас есть база символов, которая находится в переменной "CODE"



Задача, вывести символ из базы используя его порядковый номер.
Например, вывод символа номер 6 из базы:
Пример работы скрипта:

The codetable is: QWERTYUIOP
enter character number: 6
character 6 is: Y
---
CODE=Q_W_E_R_T_Y_U_I_O_P
echo "The codetable is: $CODE"
read -p "enter character number: " number

echo "character $number is:"
echo $CODE | cut -d'_' -f $number
---
CODE=Q_W_E_R_T_Y_U_I_O_P
echo "The codetable is: $CODE"
read -p "enter character number: " number

echo "character $number is:"
echo $CODE | cut -d'_' -f $number
--------------------


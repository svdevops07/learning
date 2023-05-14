# Array (массивы)

2 Groups: Ассоциативный & числовой массивы (indexed & associative)

## Числовые массивы

### Example1

tasks=(task0 task1 task2)

echo "task-1: ${tasks[0]}"  --> task-1: task0

echo "tasks: ${tasks[@]}"     --> tasks: task0 task1 task2



### Example2

for task in ${tasks[@]}
do
  command $task
done


echo "${tasks[@]:1}"        - все эл-ты со 2-го

echo "${tasks[@]:1:2}"      - 2 эл-та, начиная со 2-го

echo "${tasks[@]:(-1)}"     - послед эл-т

echo "${#tasks[@]}"         - длина всего массива

echo "${#tasks[1]}"         - длина второго эл-та

echo "${tasks[@]/*relay/}"      - выбрать все, в которых нет "relay"


tasks[10]="new_task11"          - замена одного элемента

unset tasks[10]                 - удалить элемент

unset tasks                     - удалить весь массив


## Ассоциативные массивы

declare -A versions=([kubernetes]='v.1.22.8' [terraform]='terraform_1.2.0-alpha20220413')

versions[ansible]='2.9'         - задать эл-т ассоциативного массива

echo "We restrict software: ${!versions[@]}"            - вывести все ключи массива

echo "The kube version is: ${versions[kubernetes]}"     - вывести одиноч эл-т массива


### Example3

скрипт ожидает три слова, разделенных пробелами.
Добавь в скрипт вывод вида Your phone is <третье введенное пользователем слово>


read -p "Enter your lastname, firstname and phone number with <space> delimiter: " -a account_array

echo "Your phone is ${account_array[2]}"



### Example4

определен массив animals. Используй цикл for для вывода каждого элемента массива в новой строке.


animals=('dog' 'cat' 'bird' 'hamster')

for animal in ${animals[*]}
do
  echo $animal
done



### Example4

Выбрать из входного массива 3й и 4й эл-ты

declare -a tasks

tasks=${@:3:2}

for task in $tasks
do
  bash /home/moon/prepare-and-launch $task
done




### Example5

при выводе последние два значения подсталялись из аргументов командной строки.
например: команда ./cars-list.sh solaris haval должна вывести vesta granta patriot x-ray solaris haval

cars.txt

vesta
granta 
patriot
x-ray
largus
gazel


v1

readarray -t cars_array < /home/moon/cars.txt

cars_array[${#cars_array[@]}-2]="$1"
cars_array[${#cars_array[@]}-1]="$2"

echo ${cars_array[@]}


v2

declare -a print_cars

print_cars=${@:1:2}

readarray -t cars_array < /home/moon/cars.txt


new_cars_array=${cars_array[@]:0:4}

new_cars_array+=("${print_cars[@]}")

echo ${new_cars_array[@]}
# Array (массивы)

2 Groups: Ассоциативный & числовой массивы

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
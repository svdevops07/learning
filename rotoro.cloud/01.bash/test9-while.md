# While (+ until)

## Example1


Скрипт ожидает поднятия kubectl proxy на порту 8888.


until $(curl --output /dev/null --silent --head --fail http://localhost:8888)
do
  echo -n "."
  sleep 0.5
done
echo "kubectl proxy started, continue loading"



## Example2

while true
do
  echo "1. Restart"
  echo "2. Shutdown"
  echo "3. Exit"
  read -p "Enter your option: " option

  if [ $option -eq 1 ]
  then
    shutdown -r now
  elif [ $option -eq 2 ]
  then
    shutdown now
  elif [ $option -eq 3 ]
  then
    break
  else
    continue
  fi

done


## Example3

крипт /home/moon/limit-loop.sh, который принимает два позиционных параметра, высчитывает доступные числа внутри этого промежутка и выводит каждый четный из них в новой строке в формате launch-<number>.

например: запустив команду ./limit-loop.sh 11 16, мы должны получить вывод

launch-12
launch-14
launch-16


current_launch=$1
while [[ $current_launch -le $2 ]]; do
  [ ! $(( $current_launch % 2 )) -eq 0 ] || echo "launch-$current_launch"
  current_launch=$(( $current_launch + 1 ))
done


## Example4

создадим программу-калькулятор, управляемую через меню. Разработай запускаемый скрипт /home/moon/calculator.sh, который при запуске:

Показывает меню со следующими параметрами:
Add
Subtract
Multiply
Divide
Quit
В зависимости от ввода программа должна запросить 2 числа - Number1 и Number2, а затем вывести результат в виде Answer=5.

Затем программа должна снова отображать меню, пока пользователь не выберет вариант 5 для выхода.



while true
do
  echo "1. Add"
  echo "2. Subtract"
  echo "3. Multiply"
  echo "4. Divide"
  echo "5. Quit"
  read -p "Enter the option: " opt

#  read -p "Enter two numbers: " num1 num2

  if [ $opt -eq 1 ]
  then
    read -p "Enter two numbers: " num1 num2
    ans=$(($num1+$num2))
    echo $ans
  elif [ $opt -eq 2 ]
  then
    read -p "Enter two numbers: " num1 num2
    ans=$(($num1-$num2))
    echo $ans
  elif [ $opt -eq 3 ]
  then
    read -p "Enter two numbers: " num1 num2
    ans=$(($num1*$num2))
    echo $ans
  elif [ $opt -eq 4 ]
  then
    read -p "Enter two numbers: " num1 num2
    ans=$(($num1/$num2))
    echo $ans
  elif [ $opt -eq 5 ]
  then
    break
  fi
done



while true
do
  echo "1. Add"
  echo "2. Subtract"
  echo "3. Multiply"
  echo "4. Divide"
  echo "5. Quit"

  read -p "Enter your option: " option

  if [ $option -eq 1 ]
  then
        read -p "Enter Number1: " number1
        read -p "Enter Number2: " number2
        echo Answer=$(( $number1 + $number2 ))
  elif [ $option -eq 2 ]
  then
        read -p "Enter Number1: " number1
        read -p "Enter Number2: " number2
        echo Answer=$(( $number1 - $number2 ))
  elif [ $option -eq 3 ]
  then
        read -p "Enter Number1: " number1
        read -p "Enter Number2: " number2
        echo Answer=$(( $number1 * $number2 ))
  elif [ $option -eq 4 ]
  then
        read -p "Enter Number1: " number1
        read -p "Enter Number2: " number2
        echo Answer=$(( $number1 / $number2 ))
  elif [ $option -eq 5 ]
  then
    break
  fi

done
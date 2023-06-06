# FUNCTIONS

```
$FUNCNAME - имя исполняемой функции
$RANDOM - случайное число в диапазоне 0 - 32767
```
```
########################
# Description:
#   adds two digits
# Globals:
#   None
# Arguments:
#   two input integer arguments
# Outputs:
#   None
# Returns:
#   summ as return code
########################
simple_summ() {

    return "$(( $1 + $2 ))"

}

simple_summ 1 7
summ=$?
echo $summ
```

## Example2
```
function simple_summ(){
  sum=$(( $1 + $2 ))
  echo $sum
}

result=$(simple_summ 1 7)
echo "The result is $result"
```

## Example3. Calculator
```
#!/bin/bash
read_numbers(){
  read -p "Enter Number1: " number1
  read -p "Enter Number2: " number2
}

percentage() {
  value=$1
  total=$2
  percent=$(( 100 * $value / $total ))
  echo $percent
}

while true
do
  echo "1. Add"
  echo "2. Subsctract"
  echo "3. Multiply"
  echo "4. Divide"
  echo "5. Percentage"
  echo "6. Quit"

  read -p "Enter your option: " option

  case $option in
    1)  read_numbers
        echo $(( $number1 + $number2 )) ;;

    2)
        read_numbers
        echo $(( $number1 - $number2 )) ;;

    3)
        read_numbers
        echo $(( $number1 * $number2 )) ;;

    4)
        read_numbers
        echo $(( $number1 / $number2 )) ;;

    5)
        read_numbers
        percentage $number1 $number2 ;;

    6)  break
  esac

done
```
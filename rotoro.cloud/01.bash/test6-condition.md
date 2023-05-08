# условия

if [ <condition1> ]
then
    <command1>

elif [ <condition2> ]
then 
    <command2>

else
then 
    <command3>
fi

# Conditional Operators
[ "xyz" = "xyz" ]           If string1 = string2 (true)

[ "xyz" != "xyz" ]          If string1 != string2 (false)

[ 2 -eq 2 ]                 If number1 = number2 (true)

[ 2 -ne 2 ]                 If number1 != number2 (false)

[ 10 -gt 2 ]                If number1 > number2 (true)

[ 2 -lt 3 ]                 If number1 < number2 (true)

# Additional
[ ] --> [[ ]] (только в bash)

[[ "abcxyz" = *"cx"* ]]     Если строка слева содержит "cx" (true)

[[ "xyz" = xy[zc] ]]        \
    or                       > Если третий символ "c" или "z" (true)
[[ "xyc" = xy[zc] ]]        /

[[ "xya" = xy[zc] ]]        Если третий символ "c" или "z" (false)

[[ "abc" > "bcd" ]]         Если "abc" идет после "bcd" в лексикографическом порядке (false)

[[ "abc" < "bcd" ]]         Если "abc" идет до "bcd" в лексикографическом порядке (true)

# И / ИЛИ
[ COND1 ] && [ COND2 ]      - AND   

[ COND1 ] || [ COND2 ]      - OR



[[ COND1 && COND2 ]]        - AND

[[ COND1 || COND2 ]]        - OR


[[ X -gt 5 && X -lt 10 ]]       - If X > 5 and X < 10

[[ X -gt 10 || X -lt 5 ]]       - If X > 10 or X < 5

# Conditional with Files
[ -e FILENAME ]                - True, если файл сущ

[ -d FILENAME ]                - True, если файл сущ и явл каталогом

[ -s FILENAME ]                - True, если файл сущ и размер > 0

[ -x FILENAME ]                - True, если файл исполняемый

[ -w FILENAME ]                - True, если в файл можно писать

[ -z STRING ]                  - True, если строка не сущ

[ -n STRING ]                  - True, если строка сущ

# Example1
test -n "$string" && echo "Exists" || echo "Not exist"
команда "test" похожа на квадратные скобки "[ ]"

# Example2
Скрипт должен получать два аргумента командной строки.

Если один из параметров не задан, скрипт должен выйти с сообщением Zero length. Используй команду exit для выхода.

Скрипт должен сравнить длину строк, если первая строка длинее, то написать String 1 is longer, если вторая то String 2 is longer и Strings are the same length, если они равны

Скрипт должен сравнить содержимое строк, если они одинаковые, то написать Strings have the same content, а если они не равны, то Strings are not the same



str1=$1
str2=$2

if [[ -z $str1 || -z $str2 ]]
then
  echo "Zero length"
  exit
fi

str1_len=${#str1}
str2_len=${#str2}

if [[ $str1_len -gt $str2_len ]]
then
  echo "String 1 is longer"
elif [[ $str1_len -lt $str2_len ]]
then
  echo "String 2 is longer"
elif [[ $str1_len = $str2_len ]]
then
  echo "Strings are the same length"
fi

if [[ $str1 == $str2 ]]
then
  echo "Strings have the same content"
else
  echo "Strings are not the same"
fi




string1=$1
string2=$2

if [ -z $string1 ] || [ -z $string2 ]
then
  echo "Zero length"
  exit
fi

string1_length=${#string1}
string2_length=${#string2}

if [ $string1_length -gt $string2_length ]
then
  echo "String 1 is longer"
elif [ "$string2_length" -gt "$string1_length" ]
then
  echo "String 2 is longer"
else
  echo "Strings are the same length"
fi

if [ "$string1" == "$string2" ]
then
  echo "Strings have the same content"
else
  echo "Strings are not the same"
fi


# Example3
Скрипт принимает номер месяца в качестве входных данных и печатает название соответствующего месяца.

month=$1

if [[ -z $month ]]
then
  echo "No month number"
  exit
fi

if [[ $month -lt 1 || $month -gt 12 ]]
then
  echo "Invalid month number"
  exit
else
  arr=(go
  January
  February
  March
  April
  May
  June
  July
  August
  September
  October
  Novemver
  December)

  echo ${arr[$1]}
  exit
fi
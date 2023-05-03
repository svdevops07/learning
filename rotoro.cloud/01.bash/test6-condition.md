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

# Example
test -n "$string" && echo "Exists" || echo "Not exist"
команда "test" похожа на квадратные скобки "[ ]"
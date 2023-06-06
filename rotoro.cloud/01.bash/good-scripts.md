# Script1

## Скрипт получает название папки, создает ее в текущей директории и копирует туда все файлы, добавляя суффикс _bu

 чтобы все команды в скрипте не исполнялись в реальности, а лишь проверялся их синтаксис и они были выведены на экра, нужно добавить set -vn перед первой командой скрипта.

```
#!/usr/bin/env bash

# Этот скрипт получает директорию в качестве аргумента
# Далее копируется все файлы из текущей директории в целевую, создавая копии как <filename>_bu
# Например 'my-pic.jpg' будет забэкаплен как 'my-pic.jpg_bu'

set -vn         # чтобы команды не исполнились, а лишь проверился их синтаксис и они были выведены на экран

test $# -eq 0 && echo "no folder" && exit 1

mkdir ./$1
for i in *
do
  [ -f "$i" ] && cp "$i" "./$1/${i}_bu"
done

ls -la "$1"
```


## скрипт zoidberg.sh, который получает в аргументе имя и выводит фразу: "Dr. Zoidberg Look at "
Постарайся использовать ternary operators.
```
#!/usr/bin/env bash
echo "Dr. Zoidberg Look at ${1:-Me}"
```

## скрипт reverse.sh, который получает в аргументе строку, а выводит ее задом наперед, т.е. делает реверс.
```
# ${#string} returns the length of the variable
# "${string:position:length}" string formatter
# echo -n omits the newline at the end
string=$1
for (( i=${#string}; i>=0; i-- )) do
  echo -n "${string:$i:1}"
done
```

## Правило. 
### В одинарных кавычках содержимое воспринимается как текст
### В двойных к содержимому применятся операции globbing и expansion, которые ищут паттерны, переменные и т.д. в строке
```
echo "Your shell path: $_" # Your shell path: /usr/bin/bash
echo 'Your shell path: $_' # Your shell path: $_

STR="The string  contains   multiple    spaces."

echo $STR # The string contains multiple spaces.
echo "$STR" # The string  contains   multiple    spaces.
```


## скрипт story.sh, который получает несколько аргументов и придумывает историю следующего вида:
Пример:
$ /home/moon/story.sh pin mouse cat cow car house
Changed the pin to the mouse.
Changed the mouse to the cat.
Changed the cat to the cow.
Changed the cow to the car.
Changed the car to the house.
And I started just with a pin.

```
#!/usr/bin/env bash

# 'i' initialized to 1
# 'i < $#' test passes only if 2 or more parameters
# '${!i}' indirect expansion, loop index expands to command line argument
```
for (( i=1, j=2 ; i < $# ; i++, j++ )); do
  echo "Changed the ${!i} to the ${!j}."
done

# And at least one parameter to print this:
[[ -n $1 ]] && echo "And started just with a $1."
```

## Массивы. 
```
# Прочитаем в массив строку, успользуя запятую, как разделитель
# IFS - специальная переменная, которая отвечает за разделитель полей при разбиении

lol="hi,mom,dad,cat,dog";
IFS=,
read -a myarray <<< "$lol"

echo "${myarray[@]}"


# Здесь разбили IP-адрес на октеты

IFS=. read -a ip_elements <<< "127.0.0.1"

echo "${ip_elements[*]}" # Иногда [*] и [@] ведут себя похоже, но не в этом случае
echo "${ip_elements[@]}"


# Создали строку
example=" rotoro cloud is living in the cloud"

# Это содаст массив из строки
# Поскольку 'IFS' в данный момент точка, строка не разобъется, а целиком перейдет в первый элемент массива
myarr=($example)

echo "${myarr[0]/c/C}" # Заменит первое вхождение 'c' на 'С'

echo "${myarr[0]//c/C}" # Заменит все вхождения 'c' на 'С'

echo "${myarr[0]#*c}"  # Удалит все слева до первого вхождения 'с'
echo "${myarr[0]##*c}" # Удалит слева до последнего вхождения 'с'

echo "${myarr[0]%c*}" # Удалит справа до первого вхождения 'с'
echo "${myarr[0]%%c*}" # Удалит справа до последнего вхождения 'с'
```

## скрипт pass.sh, который читает файл /etc/passwd и получает оттуда username, uid и gid
```
#!/usr/bin/env bash

while IFS=$':' read user password uid gid other
do
  users+=( "$user" )
  uids+=( "$uid" )
  gids+=( "$gid" )

  echo "$user's uid is $uid and gid is $gid"
done < /etc/passwd
```

## направления, которые помогут тебе погрузиться в глубину:

```
Pipes & Subshells
Regular Expressions
SED & AWK
Практика с " и пустыми значениями
```
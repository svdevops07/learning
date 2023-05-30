# CASE

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


↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

while true
do

  echo "1. Restart"
  echo "2. Shutdown"
  echo "3. Exit"
  read -p "Enter your option: " option

  case $option in 

    1) shutdown -r now
       ;;
    2) shutdown now
       ;;
    3) break
       ;;
    *) continue
       ;;

  esac

done





Example1
```
car=Audi

case $car in

  "Lada" | "UAZ")
    echo "${car} brand is from Russia."
    ;;

  "BMW" | "Mercedes" | "Audi")
    echo "${car} brand is from Germany."
    ;;

  "Tesla")
    echo "${car} brand is from USA."
    ;;

  "Toyota" | "Mitsubishi" | "Subaru")
    echo "${car} brand is from Japan."
    ;;

  *)
    echo "${car} is an unknown car brand"


esac
```

Example2
```
color=$1
red=`tput setaf 1`
green=`tput setaf 2`
reset=`tput sgr0`

case "$color" in
    red) echo "${red}this is red${reset}"
    ;;
    green) echo "${green}this is green${reset}"
    ;;
    *) echo "Valid options are red and green"
esac
```
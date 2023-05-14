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
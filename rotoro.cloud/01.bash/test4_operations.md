# задаем переменные
X=4
Y=5

# мат операции v1
expr $X + $Y
expr $X \* $Y

# мат операции v2
echo $((X+Y))
echo $((X*Y))

# манупулирование переменными (увелич / уменьш)
echo $((++X))   ==> 5
echo $((--X))   ==> 4

echo $((X--))   ==> 4   (--> 3)
echo $((X++))   ==> 3   (--> 4)

# числа с плавающей запятой
echo $X / $Y | bc -l    ==> .8000000

# конкатенация
X+=$Y
echo $X     ==> 45

-----------------------------------
# Exercise 1
X=$1
Y=$2

sum=$((X+Y))
echo "Sum X+Y: $sum"

diff=$((X-Y))
echo "Difference X-Y: $diff"

prod=$((X*Y))
echo "Product X*Y: $prod"

quot=$((X/Y))
echo "Quotient X/Y: $quot"

-----------------------------------
# Exercise 2
price=$(( $1 * $2 ))

echo "TOTAL: ${price}"

-----------------------------------
# Exercise 3
lenght=6
width=3

area=`expr $lenght \* $width`

echo "Sq. area is $area"

-----------------------------------
# Exercise 4
X=$1
Y=$2
Z=$3

sum=$((X+Y+Z))
avg=`echo $sum / 3 | bc -l`

echo $avg
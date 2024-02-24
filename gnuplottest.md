# ケプラー第三法則
```gnuplot {cmd=true output="html"}
set terminal svg
set grid
set xlabel "軌道長半径 a"
set ylabel "公転周期 T"
plot "planets.dat" using 2:3 pt 7 lc 7 ps 0.7 notitle
set logscale xy
replot
f(x) = K*x**p
fit f(x) "planets.dat" using 2:3 via K,p
replot f(x)
```
# カージオイド
```gnuplot {cmd=true output="html"}
set terminal svg
set parametric
set size square
r(t) = 1+cos(t)
plot [0:2*pi] r(t)*cos(t),r(t)*sin(t)
```
# 正葉曲線
```gnuplot {cmd=true output="html"}
reset
set terminal svg
set output "rose.svg"
set size  square
se nokey
set xzeroaxis
set yzeroaxis 
set xrange[-1.2:1.2]
set yrange[-1.2:1.2] 
set parametric
set trange[-10:10]
set samples 300
a=1.5
set label "a=3/2" at 0.7, 0.9 font ', 25'
plot (sin(a*t))*cos(t), (sin(a*t))*sin(t)
```

# レム二スケート
```gnuplot {cmd=true output="html"}
reset
set terminal svg
set size  ratio 0.5
se nokey
set xzeroaxis
set yzeroaxis 
set xrange[-2:2]
set yrange[-1:1] 
set parametric
set trange[0:2*pi]
set samples 10000
a=1
set label "a=1" at 1.2, 0.7 font ', 25'
plot sqrt(2*a*a*cos(2*t))*cos(t), sqrt(2*a*a*cos(2*t))*sin(t)
```
# アルキメデスの渦巻き線
```gnuplot {cmd=true output="html"}
reset
set terminal svg
set size  square
set xzeroaxis
set yzeroaxis 
set nokey
set parametric
set label "a=1, b =0.3" at 6, 14 font ', 18'
set xrange[-5*pi:5*pi]
set yrange[-5*pi:5*pi]
a=1
b=0.3
plot[-2*pi:3*pi] a*exp(b*t)*cos(t), a*exp(b*t)*sin(t)
```

# Refactoring ๐ 

## Code 1
### BAD ๋๋ฌ์ด ์ฝ๋ ๐ฃ  
> Hintโ : ๊ฒ์ํ๊ธฐ ์ฌ์ด ์ด๋ฆ์ ์ฌ์ฉํ์ธ์.  
> blastOFF๋ ๋ก์ผ ๋ฐ์ฌ๋ฅผ ์๋ฏธ. 86400000์ ํ๋ฃจ์ ๋ฐ๋ฆฌ์ด (milliseconds) ์๋ฏธ.  
> What the heck is 86400000 for?

```
setTimeout(blastOff, 86400000);
```
<br>

### GOOD ๐  
> ์ ์ฝ๋๋ฅผ ๊นจ๋ํ๊ฒ ๋ค์ ์์ฑํด ์ฃผ์ธ์.

```
const blastOffStartMilliseconds = 86400000;
setTimeout(blastOff, blastOffStartMilliseconds);
```

<br>

### ๊ณ ์น ๋ฐฉ๋ฒ๊ณผ ์ด์  โ
> ์ด๋ป๊ฒ ๊ณ ์ณค๋์ง, ์ฌ๋ก์์ ๋ฌด์์ ๋ฐฐ์์ผ ํ๋์ง ์ค๋ชํด์ฃผ์ธ์.

1. ``86400000`` ๋ผ๋ ๊ฐ์ด ์ด๋ค ๊ฐ์ธ์ง ์ธ์งํ๊ธฐ์ ์ด๋ ค์ธ ๊ฒ ๊ฐ์์ ๋ณ์๋ช์ผ๋ก ์ฌ์ฉํ์ฌ ์์ฑํ๋ค.
2. ``blastOffStartMilliseconds`` ๋ผ๋ ์ด๋ฆ์ด ๋ฌด์ฒ ๊ธธ์ด์, ์ฝ์ด๋ฅผ ์ฌ์ฉํ๋๊ฒ์ด ์ข์์ง ๊ณ ๋ฏผ์ ํ์ง๋ง ์ผ๋จ ๋ถํน์  ๋ค์์๊ฒ ๋ณด์ฌ์ฃผ๋ ๊ฒ์ด ์ค์ ์ด๋ผ๊ณ  ์๊ฐํด์ ํด๋น ๋ฐฉ๋ฒ์ ์ฌ์ฉํ๋ค.
3. ์ถ๊ฐ๋ก ``blastOff`` ๋ฅผ ๊ฒ์ํ๋ฉด ํด๋น ๋ณ์๋ ๊ฒ์๊ฒฐ๊ณผ์ ๋์ฌ ์ ์์ผ๋ ํด๋น ๋ด์ฉ์ ์๊ฐํด ์์ฑํ๋ค.
4. ๋ํ ํด๋น ์ซ์๋ ํ๋ฒ ์ ์ธ๋ ์ดํ ๋ณ๊ฒฝ๋์ง ์์ ๊ฒ ์ด๋ผ๊ณ  ์๊ฐํด ``const`` ๋ก ์์ฑํ๋ค.

<br>

## Code 2
### BAD ๋๋ฌ์ด ์ฝ๋ ๐ฃ  
> Hintโ : ์๋ฏธ์๋ ์ด๋ฆ์ ์ฌ์ฉํด์ฃผ์ธ์.

```
const yyyymmdstr = moment().format("YYYY/MM/DD");
```
<br>

### GOOD ๐
> ์ ์ฝ๋๋ฅผ ๊นจ๋ํ๊ฒ ๋ค์ ์์ฑํด ์ฃผ์ธ์.
```
const getFullDate = moment().format("YYYY/MM/DD");
```

<br>

### ๊ณ ์น ๋ฐฉ๋ฒ๊ณผ ์ด์  โ
> ์ด๋ป๊ฒ ๊ณ ์ณค๋์ง, ์ฌ๋ก์์ ๋ฌด์์ ๋ฐฐ์์ผ ํ๋์ง ์ค๋ชํด์ฃผ์ธ์.
1. ๊ฐ์ธ์ ์ผ๋ก ``yyyymmddstr`` ์ด return ๋๋ ๊ฐ์ด ๋ชํํ ๋ณด์ฌ์ ๋์์ง ์๋ค๊ณ  ์๊ฐํ๋ค.  
ํ์ง๋ง yyyy์ mm๊ณผ dd๋ฅผ ๋ชจ๋ฅด๊ฑฐ๋, ๋ค๋ฅธ๊ณณ์์ ์ฌ์ฉ์ ํ๋ค๋ฉด ๋ฌธ์ ๊ฐ ์๊ธธ ์ ์๋ค๊ณ  ์๊ฐํด์  
๋ณ์๋ง ๋ณด๊ณ  ์ด๋ค ๊ฒ์ ๊ฐ๊ณ ์ค๋์ง ๋จ์ด๋ฅผ ํด์ํด์ ์ ์ ์๋๋ก ๋ณ๊ฒฝ์ ํด๋ณด์๋ค.
2. ์ฒ์์๋ ``getDate`` ๋ก๋ ํด๋ณด์๋๋ฐ. ํผ๋์ ์ค ์ ์์ ๊ฒ์ด๋ผ ์๊ฐ๋์, ``getFullDate`` ๋ผ๊ณ  ์ด๋ฆ์ ๋ณ๊ฒฝํ๋ค.

<br>

## Code 3
### BAD ๋๋ฌ์ด ์ฝ๋ ๐ฃ  
> Hintโ : ๋ถํ์ํ๊ฒ ๋ฐ๋ณตํ์ง ๋ง์ธ์.
```
const Car = {
  carMake: "Honda",
  carModel: "Accord",
  carColor: "Blue"
};

function paintCar(car, color) {
  car.carColor = color;
}
```

<br>

### GOOD ๐
> ์ ์ฝ๋๋ฅผ ๊นจ๋ํ๊ฒ ๋ค์ ์์ฑํด ์ฃผ์ธ์.

```
const Car = {
  make: "Honda",
  model: "Accord",
  color: "Blue"
};

function getCarColor(carObj, color) {
  carObj.Color = color;
}
```

### ๊ณ ์น ๋ฐฉ๋ฒ๊ณผ ์ด์  โ
> ์ด๋ป๊ฒ ๊ณ ์ณค๋์ง, ์ฌ๋ก์์ ๋ฌด์์ ๋ฐฐ์์ผ ํ๋์ง ์ค๋ชํด์ฃผ์ธ์.
1. ``Car``๋ผ๋ Object์ ๋ด๊ธฐ๊ธฐ ๋๋ฌธ์, ๊ฐ ํค๊ฐ ์์์๋ ``car``๋ผ๋ ๋ฌธ๊ตฌ๋ฅผ ์ญ์ ํ๋ค.
2. ๊ทธ๋ฆฌ๊ณ  ``paintCar`` ๋ผ๋ function์ด ๊ฒฐ๊ณผ์ ์ผ๋ก car์ color ๊ฐ์ ๊ฐ๋ ๊ฒ์ด ์ต์ข ๋ชฉํ๋ผ๊ณ  ์๊ฐํด ํด๋น function์ ์ด๋ฆ์ ``getCarColor`` ๋ผ๊ณ  ๋ณ๊ฒฝํด ์์ฑํ๋ค.
3. ํด๋น ์ฝ๋๋ง ๋ดค์ ๋ ``getCarColor์`` ์ฒซ๋ฒ์งธ ์ธ์๊ฐ์ธ ``car``์ ๋ณ์ ํ์์ด ``object``์ธ์ง ๊ทธ ์ธ์ ๊ฒ์ธ์ง ์ ์ ์์ ๊ฒ ๊ฐ๋ค ์๊ฐ๋์ด, car๋ค์ Obj๋ฅผ ๋ถ์ฌ ``carObj``๋ฅผ ์ฌ์ฉํ๋ค.

# Refactoring 🛠

## Code 1
### BAD 더러운 코드 😣  
> Hint❕ : 검색하기 쉬운 이름을 사용하세요.  
> blastOFF는 로켓 발사를 의미. 86400000은 하루의 밀리초 (milliseconds) 의미.  
> What the heck is 86400000 for?

```
setTimeout(blastOff, 86400000);
```
<br>

### GOOD 😎  
> 위 코드를 깨끗하게 다시 작성해 주세요.

```
const blastOffStartMilliseconds = 86400000;
setTimeout(blastOff, blastOffStartMilliseconds);
```

<br>

### 고친 방법과 이유 ❔
> 어떻게 고쳤는지, 사례에서 무엇을 배워야 하는지 설명해주세요.

1. ``86400000`` 라는 값이 어떤 값인지 인지하기에 어려울 것 같아서 변수명으로 사용하여 작성했다.
2. ``blastOffStartMilliseconds`` 라는 이름이 무척 길어서, 약어를 사용하는것이 좋은지 고민을 했지만 일단 불특정 다수에게 보여주는 것이 중점이라고 생각해서 해당 방법을 사용했다.
3. 추가로 ``blastOff`` 를 검색하면 해당 변수도 검색결과에 나올 수 있으니 해당 내용을 생각해 작성했다.
4. 또한 해당 숫자는 한번 선언된 이후 변경되지 않을 것 이라고 생각해 ``const`` 로 작성했다.

<br>

## Code 2
### BAD 더러운 코드 😣  
> Hint❕ : 의미있는 이름을 사용해주세요.

```
const yyyymmdstr = moment().format("YYYY/MM/DD");
```
<br>

### GOOD 😎
> 위 코드를 깨끗하게 다시 작성해 주세요.
```
const getFullDate = moment().format("YYYY/MM/DD");
```

<br>

### 고친 방법과 이유 ❔
> 어떻게 고쳤는지, 사례에서 무엇을 배워야 하는지 설명해주세요.
1. 개인적으로 ``yyyymmddstr`` 이 return 되는 값이 명확히 보여서 나쁘지 않다고 생각한다.  
하지만 yyyy와 mm과 dd를 모르거나, 다른곳에서 사용을 한다면 문제가 생길 수 있다고 생각해서  
변수만 보고 어떤 것을 갖고오는지 단어를 해석해서 알 수 있도록 변경을 해보았다.
2. 처음에는 ``getDate`` 로도 해보았는데. 혼동을 줄 수 있을 것이라 생각되서, ``getFullDate`` 라고 이름을 변경했다.

<br>

## Code 3
### BAD 더러운 코드 😣  
> Hint❕ : 불필요하게 반복하지 마세요.
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

### GOOD 😎
> 위 코드를 깨끗하게 다시 작성해 주세요.

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

### 고친 방법과 이유 ❔
> 어떻게 고쳤는지, 사례에서 무엇을 배워야 하는지 설명해주세요.
1. ``Car``라는 Object에 담기기 때문에, 각 키값 앞에있는 ``car``라는 문구를 삭제했다.
2. 그리고 ``paintCar`` 라는 function이 결과적으로 car의 color 값을 갖는 것이 최종 목표라고 생각해 해당 function의 이름을 ``getCarColor`` 라고 변경해 작성했다.
3. 해당 코드만 봤을 때 ``getCarColor의`` 첫번째 인수값인 ``car``의 변수 타입이 ``object``인지 그 외의 것인지 알 수 없을 것 같다 생각되어, car뒤에 Obj를 붙여 ``carObj``를 사용했다.

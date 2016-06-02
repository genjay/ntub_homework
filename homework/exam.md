## 基本觀念 (共 6 題，每題 7 分，共 42 分，視答題結果部份給分)

* 你為什麼會喜歡 Ruby ? 你之前是否有其它程式語言的開發經驗? 從其它程式語言轉到 Ruby 之後，覺得最大的差別是什麼?
* ruby 可以簡單快速寫出想要的東西,ruby 內所有東西都是物件，還有他可以複蓋code
* 在學習 Ruby 的過程中，遇到覺得最難的地方是什麼?
* 他的括號可以省略，讓我很難搞懂他為什麼可以運作，但是熟了之後，卻又不排斥這功能
* Git 指令中的 `git clone` 跟 `git pull` 有什麼差別?
* git clone 是把專案整個複制回來
* git pull 是用在已複制回專案，同步最新的程式回來
* Ruby 裡的常數跟變數有什麼不同?
* 第一個字母大寫，就是常數，在ruby 內，常數可以改變
* 變數，就是隋時可以變，用來儲存運算時需要用到的值
* 
* 請問 `{ name: "eddie", age: 19 }` 跟 `{ :name => "eddie", :age => 19 }` 這兩種 Hash 的寫法有什麼差別?
* 這二懂寫法都一樣，前種是後期增加的寫法，類似json
* 
* 請簡述 Ruby 裡 public、protected 與 private 方法的差別
* public 是用來宣告class 內，可以直接使用的methods
* protected,private 無法直接使用，需要在class 內對他做呼叫
* 這二種的差別是在使用繼承或mixin 時，有一個不能被使用

## 實作題 (共 2 題，共 25 分)

* 視答題結果部份給分。
* 如果程式不會寫，也可把想法或 pseudo code 寫出來。

#### 第一題 (10 分)

有一個 BMI(Body Mass Index) 的計算方法：

```ruby
def bmi_calculator(height, weight)
  # ... 實作
end

puts bmi_calculator(178, 70)
```
```ruby
def bmi_calculator(height, weight) 
  bmi = weight / ((height.to_f/100)**2)
  bmi.round(2)
end

puts bmi_calculator(178, 70)
```
BMI 的計算公式：BMI 值 = 體重(單位：公斤) / 身高平方(單位：公尺)

輸入身高 178 公分，體重 70 公斤，期望得到答案 = 22.09 (四捨五入到小數點以下第 2 位)，請完成方法的實作內容

#### 第二題 (15 分)

有一個電影租借系統的部份功能如下：

```ruby
class Movie
  attr_accessor :name,:price
  def initialize name,price
    @name= name
    @price= price
  end
end

class Rental
  def initialize *obj
    @ids||=[]
  end
  def add_movie(obj)
    @ids<< obj
  end
  def summary
    sum||= 0 
    @ids.each do |i|
      sum +=i.price
    end
    puts "「你總共租了 #{@ids.count} 部電影，消費金額為 #{sum} 元」"
  end
end

dragon_ball = Movie.new("七龍珠", 100)  # 租金 = 100 塊
naruto = Movie.new("火影忍者", 80)      # 租金 = 80 塊

rental = Rental.new
rental.add_movie(dragon_ball)
rental.add_movie(naruto)
puts rental.summary
``` 
    

最後一行印出結果的時候，你期望結果會印出「你總共租了 2 部電影，消費金額為 180 元」，請完成中間的實作內容。

## 換句話說 (共 5 題，每題 10 分，共 50 分，視答題結果部份給分)

* 下列程式碼皆可正常運作，但可能有些有點重複、有些有點不那麼 Ruby 風味，請你用你所知道的方式，重新改寫成：
  * 較具 Ruby 風味方式
  * 較簡潔
  * 較具可讀性之程式碼
* 不需要特別縮短程式碼，以程式碼可讀性為優先。

#### 第 1 題

```ruby
result = 0
[*1..100].each do |i|
  result += i
end
puts result
```

```ruby
result = 0
[*1..100].each {|i| result += i }
puts result
```

#### 第 2 題

```ruby
profile = {name: "john"}

if profile[:company] == nil
  profile[:company] = "五倍紅寶石"
end

puts profile[:company]  # 得到「五倍紅寶石」字樣
```

```ruby
profile = {name: "john"}
profile[:company] ||= "五倍紅寶石"

puts profile[:company]  
```


#### 第 3 題

```ruby
list = [1, 2, 3, 4, 5]
result = []
list.each do |x|
  result << x * 2
end
p result    # => [2, 4, 6, 8, 10]
```

```ruby
list,result = [*1..5],[]
list.each do |x|
  result << x*2
end
p result

```
#### 第 4 題

```ruby
def is_adult?(age)
  if (age >= 18)
    return true
  else
    return false
  end
end

puts is_adult?(20)   # => true
puts is_adult?(16)   # => false
```

```ruby
def is_adult?(age)
  (age >=18)? true:false
end

puts is_adult?(20)   # => true
puts is_adult?(16)   # => false
```

#### 第 5 題

```ruby
class Cat
  def sleep
    puts "zzzzzZZZ"
  end
end

class Dog
  def sleep
    puts "zzzzzZZZ"
  end
end

lucky = Dog.new
kitty = Cat.new

lucky.sleep
kitty.sleep
```
```ruby

class Animal
  def sleep
    puts "zzzzzZZZ"
  end
end

class Cat < Animal
end
class Dog < Animal
end

lucky = Dog.new
kitty = Cat.new

lucky.sleep
kitty.sleep
```

### 注意事項

0. 可翻書、使用網路搜尋或招喚小精靈、小幫手。
1. 總分 117 分，答題時寫老師好棒棒之類的狗腿答案不會加分。
2. 請使用 `markdown` 語法答題並確認格式正確，違者該題扣 50%。
3. 程式碼請縮排正確(2 或 4 個 space)，勿使用 tab，違者該題扣分 50%。
4. 請確認程式碼均可正常執行而且結果正確，若不可執行該題得 0 分。
5. 請將作答內容存成 `學號.md`，並將檔案 email 至 eddie@5xruby.tw ；若明顯看得出來「參考」情況，將視情況將「參考者」與「被參考者」之總分扣 30 ~ 40 分。

# Swift

 
<a name="string-autorelease"></a>
## Что произойдет если сначала нажать на кнопку 1 а потом на кнопку 2?
```objectivec
- (IBAction)btn1DidTouch:(id)sender {
	_string = [[[NSString alloc] initWithFormat:@"v=%i", rand()] autorelease];
}
- (IBAction)btn2DidTouch:(id)sender {
	NSLog(@"_string is equal to ‘%@’", _string);
}
```


## Что произойдет при исполнении следующего кода?
```objectivec
Ball *ball = [[[[Ball alloc] init] autorelease] autorelease];
```


<a name="hello-world"></a>
## Выведется ли в дебагер Hello world? Почему?
```objectivec
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
  dispatch_sync(dispatch_get_main_queue(), ^{
    NSLog(@"Hello world");
  });
  /* Another implementation */
  return YES;
}
```

## Что выведется в консоль?
```objectivec
NSObject *object = [NSObject new];
dispatch_async(dispatch_get_main_queue(), ^ {
  NSLog(@"A %d", [object retainCount]);
  dispatch_async(dispatch_get_main_queue(), ^ {
    NSLog(@"B %d", [object retainCount]);
  });
  NSLog(@"C %d", [object retainCount]);
});
NSLog(@"D %d", [object retainCount]);

```

<a name="задача-про-банерокрутилку"></a>
## Задача про банерокрутилку
Из заданного списка вывести поочередно, рандомно, а главное, без повторений, все его элементы.


<a name="задача-на-регулярное-выражение"></a>
## Задача на регулярное выражение
В системе авторизации есть следующее ограничение на формат логина: он должен начинаться с латинской буквы, может состоять из латинских букв, цифр, точки и минуса и должен заканчиваться латинской буквой или цифрой. Минимальная длина логина — 1 символ. Максимальная — 20 символов.


<a name="заполнить-строку-буквами-a"></a>
## Заполнить строку буквами А, чтобы не делать миллионы итераций
```objectivec
NSString *str = @"a";
for (int i = 0; i< 5000000; i++) {
  str = [str stringByAppendingString:@"a"];
}
```



<a name="что-не-так-с-этим-кодом"></a>
## Что не так с этим кодом?
```objectivec
[[[SomeClass alloc] init] init];
```

<a name="какой-метод-вызовется"></a>
## Какой метод вызовется: класса A или класса B?
```objectivec
@interface A : NSObject
- (void)someMethod;
@end

@implementation A
- (void)someMethod {
  NSLog(@"This is class A");
}
@end

@interface B : A
@end

@implementation B
- (void)someMethod {
  NSLog(@"This is class B");
}
@end

@interface C : NSObject
@end

@implementation C
- (void)method {
  A *a = [B new];
  [a someMethod];
}
@end
```

<a name="int8_t-matrix"></a>
## Допустимо ли?
```c
int8_t matrix [2048][2024]`
```

<a name="memory-for-structs"></a>
## Одинаковую ли память занимают эти структуры и почему так?

```c
struct StructA {
  int32_t a;
  char b;
  char c;
};

struct StructB {
  char b;
  int32_t a;
  char c;
};
```

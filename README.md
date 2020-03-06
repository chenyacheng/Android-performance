# Android性能

1，在Activity,Fragment等生命周期方法中和Adapter重写类中，避免有些频繁触发的逻辑方法中存在大量对象分配

2，懒加载和缓存机制。访问网络的耗时操作启动一个新线程来做，而不要再UI线程来做，单例最好懒加载，Fragment也最好懒加载

3，UI线程不做耗时操作，耗时操作放在子线程处理

4，布局文件要尽可能的优化，减少布局的解析时间。尽量减少布局的嵌套层次，尽量使用include，merge，ViewStub

5，减少同一时刻的动画执行次数

6，自定义view时，减少onMeasure，onLayout，onDraw等的调用次数，注意避免有些频繁触发的逻辑方法中存在大量对象分配

7，对象引用之后要及时回收

8，减少冗余资源和代码逻辑的使用

9，减少没必要的背景、暂时不显示的View设置为GONE而不是INVISIBLE、自定义View的onDraw方法设置canvas.clipRect()指定绘制区域或通过canvas.quickreject()减少绘制区域等。

10，尽量避免在多次for循环中频繁分配对象

11，避免在自定义View的onDraw()方法中执行复杂的操作及创建对象（譬如Paint的实例化操作不要写在onDraw()方法中等）

12，对于并发下载等类似逻辑的实现尽量避免多次创建线程对象，而是交给线程池处理

13，使用foreach代替for i

14，尽量少的声明全局变量

15，声明全局静态变量，一定要加final声明

16，声明非静态的全局变量，最好不要初始化任何值，在使用到的地方，在进行初始化

17，函数中若干次使用全局变量，应该将全局变量赋值给本地变量，然后直接使用本地变量

18，能用Int，不要使用浮点数

19，能用乘法不用除法

20，尽量避免使用geter和setter方法

21，在Activity的onCreate函数中，尽量做少的事

22，在Activity中声明的静态数组或者静态代码块，重构到单独的一个类里

23，Activity启动后开始进行异步线程的加载，最好delay一下。再开启线程

24，对于存在于集合中的Bean对象，尽可能少的声明变量。能用int 就不要用long.声明的string等复杂变量，最好不要进行初始化

25，使用线程，一定要给它传一个名字，然后需要定义线程的优先级

26，在使用集合的时候，优先选择SparseArray

27，尽量避免使用枚举

28，工具方法尽量写成是静态方法

29，线程间同步尽量使用开销小的同步锁

30，在使用集合类的时候，如果已知数据的规模，在初始化的时候，就设定好默认大小

31，私有内部类访问外部类的私有变量，要将变量修改为包继承权限，在私有内部类中，考虑用包访问权限替代私有访问权限

32，对于开销大的算法，且不止是执行一次的，要使用缓存策略

33，避免在绘制或者解析布局的时候，分配对象。例如onDraw方法

34，不要给布局写无用的参数，例如RelativeLayout，写layout_weight属性

35，尽量减少布局的嵌套层数。例如包含一个ImageView和TextView的线性布局，可以用CompoundDrawable的TextView来代替

36，尽量用Android提供的SparseArray来代替HashMap

37，如果LinearLayout用于嵌套的layout空间计算，它的android:baselineAligned设置为false,可以加速layout计算

38，尽量避免嵌套的使用layout_weight,那样会影响执行效率

39，如果为rootView设置了背景，那么会先用Theme指定的背景绘制一遍，然后才用指定的背景绘制，这叫做"overdraw",可以通过theme的background为null来避免

40，不要有无用的任何资源，代码或者文件

41，一个Activity中使用同一个View.onClickListener()处理所有的业务逻辑

42，数据一定要校验，如用户填写的日期时间数据、电话号码数据等

43，不要随意的使用stingA=StringB+StringC的写法，有大量拼接操作的地方用StringBuilder代替

44，有些能用文件操作的，尽量采用文件操作，文件操作的速度比数据库的操作要快10倍左右

45，避免重复点击和快速点击

46，尽量避免static成员变量引用资源耗费过多的实例,比如Context

47，应用开发中自定义View的时候，交互部分，千万不要写成线程不断刷新界面显示，而是根据TouchListener事件主动触发界面的更新

48，如果ImageView的图片是来自网络，进行异步加载

49，保证Cursor 占用的内存被及时的释放掉，而不是等待GC来处理。并且 Android明显是倾向于编 程者手动的将Cursor close掉

50，软键盘的弹出控制，不要让其覆盖输入框

51，使用styles，复用样式定义

52，复杂布局使用RelativeLayout

53，自适应屏幕，使用dp替代pix

54，使用animation-list制作动画效果
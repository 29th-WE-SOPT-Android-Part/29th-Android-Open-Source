# Inflate View in Programing Code



## 개요

> **서버 통신으로 가져온 리스트 데이터들이 Chip으로 보여주게 해주세요. (요구사항)**

저는 현재 SOPT를 하고 있지 않지만 27기, 28기 SOPT Android를 했던 송훈기라고 합니다.

위에 보이는 요구사항 예시는 앞으로 여러분들이 프로젝트를 진행하면서 충분히 받을 수 있는 요구사항입니다.

위와 같은 상황은 **동적으로 View가 보여져야 하는 경우**를 의미하겠지요

기존에 하던 방식인 XML에 Chip 태그들 적고 하게 되면 정적인 갯수밖에 보여지지 않을 것입니다.

이는 즉, Programming Code에서 View를 보여져야 하는 순간을 의미하게 되겠지요. (XML로는 정적인 갯수밖에 처리할 수 없으니까 말이죠.)

그떄 어떻게 해야하는지! , 뭐 이건 하나의 예시지만 Android에서 View를 표현하기 위해선 어떤 것들이 필요한지 이런 기본적인 개념도 차근차근히 알 수 있게 적어놓겠습니다.

## 개념

### XML 

> **예를 들어 , Activity 하나를 생성한다고 생각해볼까요?** 

 Activity를 생성한 프로젝트에 추가된 파일은 **Activity를 표현하는 *xml 파일*** , **Activity이 보여지고 기능할 수 있도록 해주는 *Java 파일***

이렇게 총 2개가 생성될 것입니다.

이렇듯이 Android에서 *View* , *ViewGroup* ,*Widget* 등, 이를 표현하기 위해선 *xml*과 이를 구현하는 *java*파일이 각각 필요하다는 것입니다.  

여기까지 인식을 했다면 반은 왔습니다.

## 응용

> **Chip을 만들어봅시다**

이제 *XML*과 *java*파일의 관계를 대충은 알게 되었습니다.

그럼 이제 다시 예제로 돌아와 Chip을 동적으로 추가하는 방법을 가지고 얘기를 해보겠습니다.

가장 먼저, Chip을 표현할 *XML* 파일이 존재해야합니다.

```kotlin
<?xml version="1.0" encoding="utf-8"?>
<com.google.android.material.chip.Chip xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    style="@style/Widget.MaterialComponents.Chip.Action"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:gravity="center"
    android:includeFontPadding="false"
    android:textSize="12sp"
    android:textAlignment="center"
    android:theme="@style/Widget.MaterialComponents.Chip.Choice"
    app:chipStrokeColor="@color/white" />
```

Chip은 [MaterialDesign](https://material.io/design)에 대해서 알아보면 더 자세히 알 수 있습니다.

이렇게 Chip XML파일을 만들었다면 다음에 이녀석을 *1) 어떻게*  *2) 어떤 크기* *3) 어떤 기능* 담아서  해야할 지 코드에 작성해야합니다.

Chip에 대해서 아는 분은 알겠지만 이는 특정 Layout에서 사용되는 Widget입니다. 특정 Layout에 하위에 존재한다는 의미이기도 하죠

그렇기에 저는 *확장함수* 를 이용해 이를 표현하는 로직을 함수화 할 것입니다. ( 어차피 확장함수는 나중에 배우니 지금은 대충 이해해도 됩니다. )

```kotlin
fun LinearLayout.addChip(chipText: String) { // 1
    val chip = LayoutInflater.from(context).inflate(R.layout.view_chip, null) as Chip // 2

    val layoutParams = ViewGroup.MarginLayoutParams( // 3
        ViewGroup.MarginLayoutParams.WRAP_CONTENT,
        ViewGroup.MarginLayoutParams.WRAP_CONTENT
    )
    chip.text = chipText // 4
    layoutParams.rightMargin = context.dpToPixel(4) // 5
    addView(chip,layoutParams) // 6
}
```

함수화된 Chip 추가하는 함수입니다.

1) Chip 특정 레이아웃의 속해서 Widget의 형태로 보여진다고 얘기했습니다. 그래서 저는 Chip 쓰고자 하는 Layout인 LinearLayout에 확장함수를 만들어 Chip을 추가하는 함수를 만들었습니다.
2) Fragment나 Activity를 쓰면서 *ViewBinding*을 공부하신 여러분은 알겠지만 *inflate*라는 단어를 참 많이 사용합니다. inflate의 뜻은 xml로 되어 있던 내용들이 메모리에 로딩되어 객체화 하는 과정이라고 생각하면 편할 것입니다. 즉, xml로 된 내용을 inflate함으로써 그 객체를 사용할 수 있게 되는 것입니다. 이 경우엔 변수 chip에 담아뒀기 때문에 이후 chip변수를 활용해 inflate된 객체를 사용할 수 있게 됩니다.  
3) Param이라는 단어가 등장했는데 어려울 거 없습니다. 우리는 Chip이 어떻게 생기고 객체화 까지는 했지만, 이녀석이 어떤 크기인지는 정하지 않았습니다. 그렇기 떄문에 그 크기를 결정해주는 것이 Param입니다. 이는 Layout의 특성에 따라 다양한 Param을 적용해야하니 찾아보고 사용하시면 될 것입니다. ( 예제에선 WRAP_CONTENT로 크기에 맞게끔 적용했습니다. )
4) 통신을 통하거나 동적으로 등장한 제목을 넣어주는 과정입니다
5) Padding과 Margin 또한 Param에 적용해 간격을 떨어뜨릴 수 있습니다.
6) 마지막으로 layout의 addView 메서드를 통해 Chip객체와 Param을 적용함으로써 화면에 보여지게 됩니다.

## 마무리

여러분들이 사용하는 Activity나 Fragment Button등 모든 것은 이와 같은 요소들을 사용해 화면에 보여지도록 합니다.

예시에선 Chip이자만 동적으로 처리되어야 하는 무언가가 있을 땐 이걸 참고해서 작성할 수 있었으면 하는 바램입니다.




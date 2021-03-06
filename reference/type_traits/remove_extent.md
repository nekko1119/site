#remove_extent
* type_traits[meta header]
* std[meta namespace]
* class template[meta id-type]
* cpp11[meta cpp]

```cpp
namespace std {
  template <class T>
  struct remove_extent {
    typedef … type;
  };

  template <class T>
  using remove_extent_t = typename remove_extent<T>::type; // C++14
}
```

##概要
配列型`T`から次元を除去する。


##効果
`remove_extent`は、型`T`が、何らかの型`U`の配列型である場合は`U`型を、そうでなければ型`T`をメンバ型`type`として定義する。


##例
```cpp
#include <type_traits>

static_assert(std::is_same<
        std::remove_extent<int>::type,
        int
    >::value,
    "transform int to int");

static_assert(std::is_same<
        std::remove_extent<const int[2]>::type,
        const int
    >::value,
    "transform const int[2] to const int");

static_assert(std::is_same<
        std::remove_extent<int[2][4]>::type,
        int[4]
    >::value,
    "transform int[2][4] to int[4]");

static_assert(std::is_same<
        std::remove_extent<int[][2]>::type,
        int[2]
    >::value,
    "transform int[][2] to int[2]");

int main() {}
```

###出力
```
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation.md#clang): 3.0
- [GCC, C++11 mode](/implementation.md#gcc): 4.3.6
- [Visual C++](/implementation.md#visual_cpp): 9.0 (std::tr1), 10.0, 11.0, 12.0, 14.0
	- `remove_extent_t`は12.0から


##参照
- [N3546 TransformationTraits Redux](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3546.pdf)
- [N3655 TransformationTraits Redux, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3655.pdf)


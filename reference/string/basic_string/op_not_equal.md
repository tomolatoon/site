# operator!=
* string[meta header]
* std[meta namespace]
* function template[meta id-type]

```cpp
namespace std {
  template <class CharT, class Traits, class Allocator>
  bool
    operator!=(const basic_string<CharT, Traits, Allocator>& a,
               const basic_string<CharT, Traits, Allocator>& b);          // (1) C++03
  template <class CharT, class Traits, class Allocator>
  bool
    operator!=(const basic_string<CharT, Traits, Allocator>& a,
               const basic_string<CharT, Traits, Allocator>& b) noexcept; // (1) C++14
  template <class CharT, class Traits, class Allocator>
  constexpr bool
    operator!=(const basic_string<CharT, Traits, Allocator>& a,
               const basic_string<CharT, Traits, Allocator>& b) noexcept; // (1) C++20


  template <class CharT, class Traits, class Allocator>
  bool
    operator!=(const CharT* a,
               const basic_string<CharT, Traits, Allocator>& b); // (2) C++03
  template <class CharT, class Traits, class Allocator>
  constexpr bool
    operator!=(const CharT* a,
               const basic_string<CharT, Traits, Allocator>& b); // (2) C++20

  template <class CharT, class Traits, class Allocator>
  bool
    operator!=(const basic_string<CharT, Traits, Allocator>& a,
               const CharT* b);                                  // (3) C++03
  template <class CharT, class Traits, class Allocator>
  constexpr bool
    operator!=(const basic_string<CharT, Traits, Allocator>& a,
               const CharT* b);                                  // (3) C++20
}
```

## 概要
`basic_string`オブジェクトの非等値比較を行う。


## 要件
- (3) パラメータ`b`が、[`Traits::length`](/reference/string/char_traits/length.md)`(b) + 1`の要素数を持つ`CharT`文字型の配列を指していること


## 戻り値
- (1) `!(a == b)`
- (2) `b != a`
- (3) `a.`[`compare`](compare.md)`(b) != 0`


## 例
```cpp example
#include <iostream>
#include <string>

int main()
{
  std::string a = "abc";
  std::string b = "abcd";

  if (a != b) {
    std::cout << "not equal" << std::endl;
  }
  else {
    std::cout << "equal" << std::endl;
  }
}
```

### 出力
```
not equal
```

## 参照
- [LWG2064 - More `noexcept` issues in `basic_string`](https://wg21.cmeerw.net/lwg/issue2064)
- [P0980R1 Making `std::string` constexpr](https://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p0980r1.pdf)

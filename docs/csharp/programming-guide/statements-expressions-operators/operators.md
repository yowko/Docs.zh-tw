---
title: 運算子 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: e9518dcf2a9facfdc46c2f6245184ea2da95b819
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238997"
---
# <a name="operators-c-programming-guide"></a>運算子 (C# 程式設計手冊)
在 C# 中，「 *運算子* 」(Operator) 是程式的元素，這類元素會套用至運算式或陳述式中的一個或多個「 *運算元* 」(Operand)。 只使用一個運算元的運算子稱為`++`「一元」 `new`(Unary) 運算子，例如遞增運算子 ( *) 或* 。 使用兩個運算元的運算子稱為`+`「二元」`-`(Binary) 運算子，例如算術運算子 (`*`、`/`、 *及* )。 還有一種運算子稱為條件運算子 (`?:`)，它會使用三個運算元而且是 C# 中唯一的三元運算子。  
  
 下列 C# 陳述式包含一個一元運算子和一個運算元。 遞增運算子 `++`會修改運算元 `y`的值。  
  
 [!code-csharp[csProgGuideStatements#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/operators_1.cs)]  
  
 下列 C# 陳述式包含兩個二元運算子，這兩個運算子各有兩個運算元。 指派運算子 `=`的運算元為整數變數 `y` 和運算式 `2 + 3` 。 運算式 `2 + 3` 本身包含加法運算子和兩個運算元 `2` 和 `3`。  
  
 [!code-csharp[csProgGuideStatements#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/operators_2.cs)]  
  
## <a name="operators-evaluation-and-operator-precedence"></a>運算子、評估和運算子優先順序  
 運算元可以是由任何長度的程式碼撰寫而成的有效運算式，而且可以包含任何數量的子運算式。 在包含多個運算子的運算式中，套用運算子的順序取決於「 *運算子優先順序*」(Operator Precedence)、「 *順序關聯性*」(Associativity) 以及括號。  
  
 每個運算子都有定義的優先順序。 在包含多個運算子且運算子具有不同優先順序層級的運算式中，運算子的優先順序決定評估運算子的順序。 例如，下列陳述式會將 3 指派給 `n1`。  
  
 `n1 = 11 - 2 * 4;`  
  
 因為乘法的優先順序高於減法，所以會先執行乘法。  
  
 下表根據運算子所執行的運算類型，將運算子加以分類。 分類是依照優先順序列出。  
  
 **主要運算子**  
  
|運算式|說明|  
|----------------|-----------------|  
|x[.](../../../csharp/language-reference/operators/member-access-operator.md)y<br /><br /> x?.y|成員存取<br /><br /> 條件式成員存取|  
|f[(x)](../../../csharp/language-reference/operators/invocation-operator.md)|方法和委派叫用|  
|a[&#91;x&#93;](../../../csharp/language-reference/operators/index-operator.md)<br /><br /> a?[x]|陣列和索引子存取<br /><br /> 條件式陣列和索引子存取|  
|x[++](../../../csharp/language-reference/operators/increment-operator.md)|後置遞增|  
|x[--](../../../csharp/language-reference/operators/decrement-operator.md)|後置遞減|  
|[new](../../../csharp/language-reference/keywords/new-operator.md) T(...)|建立物件和委派|  
|`new` T(...){...}|使用初始設定式建立物件。 請參閱[物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。|  
|`new` {...}|匿名物件初始設定式。 請參閱[匿名型別](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。|  
|`new` T[...]|建立陣列。 請參閱[陣列](../../../csharp/programming-guide/arrays/index.md)。|  
|[typeof](../../../csharp/language-reference/keywords/typeof.md)(T)|取得 T 的 System.Type 物件|  
|[checked](../../../csharp/language-reference/keywords/checked.md)(x)|在核取的內容中評估運算式|  
|[unchecked](../../../csharp/language-reference/keywords/unchecked.md)(x)|在未核取的內容中評估運算式|  
|[default](../../../csharp/language-reference/keywords/default.md) (T)|取得類型 T 的預設值|  
|[delegate](../../../csharp/language-reference/keywords/delegate.md) {}|匿名函式 (匿名方法)|  
  
 **一元運算子**  
  
|運算式|說明|  
|----------------|-----------------|  
|[+](../../../csharp/language-reference/operators/addition-operator.md)x|身分識別|  
|[-](../../../csharp/language-reference/operators/subtraction-operator.md)x|否定|  
|[\!](../../../csharp/language-reference/operators/logical-negation-operator.md)x|邏輯否定|  
|[~](../../../csharp/language-reference/operators/bitwise-complement-operator.md)x|位元否定|  
|[++](../../../csharp/language-reference/operators/increment-operator.md)x|前置遞增|  
|[--](../../../csharp/language-reference/operators/decrement-operator.md)x|前置遞減|  
|[(T)](../../../csharp/language-reference/operators/invocation-operator.md)x|x 明確轉換成類型 T|  
  
 **乘法類運算子**  
  
|運算式|說明|  
|----------------|-----------------|  
|[*](../../../csharp/language-reference/operators/multiplication-operator.md)|乘法|  
|[/](../../../csharp/language-reference/operators/division-operator.md)|除號|  
|[%](../../../csharp/language-reference/operators/modulus-operator.md)|餘數|  
  
 **加法類運算子**  
  
|運算式|說明|  
|----------------|-----------------|  
|x [+](../../../csharp/language-reference/operators/addition-operator.md) y|加法、字串串連、委派組合|  
|x [-](../../../csharp/language-reference/operators/subtraction-operator.md) y|減法、委派移除|  
  
 **移位運算子**  
  
|運算式|說明|  
|----------------|-----------------|  
|x [<\<](../../../csharp/language-reference/operators/left-shift-operator.md) y|左移|  
|x [>>](../../../csharp/language-reference/operators/right-shift-operator.md) y|右移|  
  
 **關係和型別運算子**  
  
|運算式|說明|  
|----------------|-----------------|  
|x [\<](../../../csharp/language-reference/operators/less-than-operator.md) y|小於|  
|x [>](../../../csharp/language-reference/operators/greater-than-operator.md) y|大於|  
|x [\<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) y|小於或等於|  
|x [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) y|大於或等於|  
|x [is](../../../csharp/language-reference/keywords/is.md) T|如果 x 為 T 則傳回 true，否則傳回 false|  
|x [as](../../../csharp/language-reference/keywords/as.md) T|傳回類型 T 的 x，如果 x 不是 T 則傳回 null|  
  
 **等號比較運算子**  
  
|運算式|說明|  
|----------------|-----------------|  
|x [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) y|等於|  
|x [!=](../../../csharp/language-reference/operators/not-equal-operator.md) y|不相等|  
  
 **邏輯、條件和 Null 運算子**  
  
|分類|運算式|說明|  
|--------------|----------------|-----------------|  
|邏輯 AND|x [&](../../../csharp/language-reference/operators/and-operator.md) y|整數位元 AND、布林邏輯 AND|  
|邏輯 XOR|x [^](../../../csharp/language-reference/operators/xor-operator.md) y|整數位元 XOR、布林邏輯 XOR|  
|邏輯 OR|x [&#124;](../../../csharp/language-reference/operators/or-operator.md) y|整數位元 OR、布林邏輯 OR|  
|條件式 AND|x [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) y|只有在 x 為 true 時評估 y|  
|條件式 OR|x [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) y|只有在 x 為 false 時評估 y|  
|Null 聯合|x [??](../../../csharp/language-reference/operators/null-coalescing-operator.md) Y|如果 x 為 null 則判斷值為 y，否則判斷值為 x|  
|條件式|x [?](../../../csharp/language-reference/operators/conditional-operator.md) y : z|如果 x 為 true 則判斷值為 y；如果 x 為 false 則判斷值為 z|  
  
 **指派和匿名運算子**  
  
|運算式|說明|  
|----------------|-----------------|  
|[=](../../../csharp/language-reference/operators/assignment-operator.md)|指派|  
|x op= y|複合指派。 支援這些運算子：[+=](../../../csharp/language-reference/operators/addition-assignment-operator.md)、[-=](../../../csharp/language-reference/operators/subtraction-assignment-operator.md)、[*=](../../../csharp/language-reference/operators/multiplication-assignment-operator.md)、[/=](../../../csharp/language-reference/operators/division-assignment-operator.md)、[%=](../../../csharp/language-reference/operators/modulus-assignment-operator.md)、[&=](../../../csharp/language-reference/operators/and-assignment-operator.md)、[&#124;=](../../../csharp/language-reference/operators/or-assignment-operator.md)、[^=](../../../csharp/language-reference/operators/xor-assignment-operator.md)、[<\<=](../../../csharp/language-reference/operators/left-shift-assignment-operator.md)、[>>=](../../../csharp/language-reference/operators/right-shift-assignment-operator.md)|  
|(T x) [=>](../../../csharp/language-reference/operators/lambda-operator.md) y|匿名函式 (Lambda 運算式)|  
  
## <a name="associativity"></a>順序關聯性  
 當運算式中有兩個以上具有相同優先順序的運算子時，會根據順序關聯性評估這些運算子。 左向關聯運算子會依由左至右的順序進行評估。 例如， `x * y / z` 會判斷值為 `(x * y) / z`。 右向關聯運算子會依由右至左的順序進行評估。 例如，指派運算子就是右向關聯。 如果不是的話，下列程式碼將會產生錯誤。  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 另一個範例是右向關聯的三元運算子 ([?:](../../../csharp/language-reference/operators/conditional-operator.md))。 大部分的二元運算子都是左向關聯。  
  
 不論運算式中的運算子是左向關聯還是右向關聯，都會由左至右先行評估每個運算式的運算元。 下列範例將說明運算子和運算元的評估順序。  
  
|陳述式|評估的順序|  
|---------------|-------------------------|  
|`a = b`|a, b, =|  
|`a = b + c`|a, b, c, +, =|  
|`a = b + c * d`|a, b, c, d, *, +, =|  
|`a = b * c + d`|a, b, c, *, d, +, =|  
|`a = b - c + d`|a, b, c, -, d, +, =|  
|`a += b -= c`|a, b, c, -=, +=|  
  
## <a name="adding-parentheses"></a>加入括號  
 您可以使用括號變更運算子優先順序和順序關聯性強制執行的順序。 例如， `2 + 3 * 2` 正常情況下會判斷值為 8，這是因為乘法類運算子的優先順序高於加法類運算子。 但是，如果您將運算式撰寫為 `(2 + 3) * 2`，則會先評估加法再評估乘法，而得到的結果會是 10。 下列範例將說明以括號括住之運算式中的評估順序。 如先範例所示，套用運算子之前會先評估運算元。  
  
|陳述式|評估的順序|  
|---------------|-------------------------|  
|`a = (b + c) * d`|a, b, c, +, d, *, =|  
|`a = b - (c + d)`|a, b, c, d, +, -, =|  
|`a = (b + c) * (d - e)`|a, b, c, +, d, e, -, *, =|  
  
## <a name="operator-overloading"></a>運算子多載  
 您可以變更自訂類別和結構的運算子行為。 這個程序稱為「 *運算子多載*」(Operator Overloading)。 如需詳細資訊，請參閱[多載運算子](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)和 [operator](../../../csharp/language-reference/keywords/operator.md) 關鍵字文章。  
  
## <a name="related-sections"></a>相關章節  
 如需詳細資訊，請參閱[運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md)[C# 運算子](../../../csharp/language-reference/operators/index.md)。  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [陳述式、運算式和運算子](../../../csharp/programming-guide/statements-expressions-operators/index.md)

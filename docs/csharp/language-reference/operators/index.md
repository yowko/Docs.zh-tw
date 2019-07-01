---
title: C# 運算子 - C# 參考
ms.date: 04/30/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 7d8ee9be8f399bca0aace61d344b19094c9518b0
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401458"
---
# <a name="c-operators-c-reference"></a>C# 運算子 (C# 參考)

C# 提供內建型別支援的數個預先定義運算子。 例如，[算術運算子](arithmetic-operators.md)會執行含內建數值型別運算元的算術運算，而[布林邏輯運算子](boolean-logical-operators.md)會執行含 [bool](../keywords/bool.md) 運算元的邏輯運算。

使用者定義型別可以多載特定運算子，以定義該型別運算元的對應行為。 如需詳細資訊，請參閱[運算子](../keywords/operator.md)關鍵字文章。

下面各節列出 C# 運算子，從最高優先順序開始列到最低。 每個區段中的運算子會共用相同的優先順序層級。

## <a name="primary-operators"></a>主要運算子

這些是最高優先順序的運算子。

[x.y](member-access-operators.md#member-access-operator-) – 成員存取。

[x?.y](member-access-operators.md#null-conditional-operators--and-) – null 條件成員存取。 如果左運算元評估為 `null`，則傳回 `null`。

[x?[y]](member-access-operators.md#null-conditional-operators--and-) - Null 條件式陣列項目，或型別索引子存取。 如果左運算元評估為 `null`，則傳回 `null`。

[f(x)](member-access-operators.md#invocation-operator-) – 方法呼叫，或委派叫用。

[&#91;x&#93;](member-access-operators.md#indexer-operator-) – 陣列項目，或型別索引子存取。

[x++](arithmetic-operators.md#increment-operator-) – 後置遞增。 傳回 x 的值，然後利用大於 x 值的值 (通常會加上整數 1) 更新儲存位置。

[x--](arithmetic-operators.md#decrement-operator---) – 後置遞減。 傳回 x 的值，然後利用小於 x 值的值 (通常會減去整數 1) 更新儲存位置。

[new](new-operator.md) – 型別執行個體化。

[typeof](type-testing-and-conversion-operators.md#typeof-operator) - 傳回代表運算元的 <xref:System.Type> 物件。

[checked](../keywords/checked.md) – 啟動整數作業的溢位檢查。

[unchecked](../keywords/unchecked.md) – 停用整數作業的溢位檢查。 這是預設編譯器行為。

[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) - 產生類型 T 的預設值。

[nameof](../keywords/nameof.md) - 取得變數、型別或成員的簡單 (未限定) 名稱，作為常數字串。

[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – 宣告並傳回委派執行個體。

[sizeof](../keywords/sizeof.md) – 傳回型別運算元的大小 (以位元組為單位)。

[stackalloc](stackalloc.md) -　配置堆疊上的記憶體區塊。

[->](pointer-related-operators.md#pointer-member-access-operator--) - 指標間接取值結合成員存取。

## <a name="unary-operators"></a>一元運算子

這些運算子具有的優先順序高於下一個區段且低於前一個區段。

[+x](addition-operator.md) – 傳回 x 的值。

[-x](subtraction-operator.md) – 數值否定。

[\!x](boolean-logical-operators.md#logical-negation-operator-) – 邏輯否定。

[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – 位元補數。

[++x](arithmetic-operators.md#increment-operator-) – 前置遞增。 傳回 x 的值之前，利用大於 x 值的值 (通常會加上整數 1) 更新儲存位置。

[--x](arithmetic-operators.md#decrement-operator---) – 前置遞減。 更新儲存體位置之後，傳回 x 減一的 x 值 (通常減去整數 1)。

[(T)x](type-testing-and-conversion-operators.md#cast-operator-) – 型別轉換。

[await](../keywords/await.md) – 等候 `Task`。

[&x](pointer-related-operators.md#address-of-operator-) - 變數的位址。

[*x](pointer-related-operators.md#pointer-indirection-operator-) - 指標間接取值或取值 (Dereference)。

[true 運算子](true-false-operators.md) - 傳回 [bool](../keywords/bool.md) 值 `true` 以指出運算元必然為 true。

[false 運算子](true-false-operators.md) - 傳回 [bool](../keywords/bool.md) 值 `true`，以指出運算元必然為 false。

## <a name="multiplicative-operators"></a>乘法類運算子

這些運算子具有的優先順序高於下一個區段且低於前一個區段。

[x * y](arithmetic-operators.md#multiplication-operator-) – 乘法。

[x / y](arithmetic-operators.md#division-operator-) – 除法。 如果運算元都是整數，則結果會截斷趨近於零的整數 (例如，`-7 / 2 is -3`)。

[x % y](arithmetic-operators.md#remainder-operator-) – 餘數。 如果運算元都是整數，這會傳回 x 除以 y 的餘數。  若為 `q = x / y` 和 `r = x % y`，則為 `x = q * y + r`。

## <a name="additive-operators"></a>加法類運算子

這些運算子具有的優先順序高於下一個區段且低於前一個區段。

[x + y](arithmetic-operators.md#addition-operator-) – 加法。

[x – y](arithmetic-operators.md#subtraction-operator--) – 減法。

## <a name="shift-operators"></a>移位運算子

這些運算子具有的優先順序高於下一個區段且低於前一個區段。

[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – 位元向左移位並使用右邊的零填滿。

[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – 位元向右移位。 如果左運算元是 `int` 或 `long`，則以正負號位元填入左位元。 如果左運算元是 `uint` 或 `ulong`，則以零填入左位元。

## <a name="relational-and-type-testing-operators"></a>關係和類型測試運算子

這些運算子具有的優先順序高於下一個區段且低於前一個區段。

[x \< y](comparison-operators.md#less-than-operator-) – 小於 (如果 x 小於 y，則為 true)。

[x > y](comparison-operators.md#greater-than-operator-) – 大於 (如果 x 大於 y，則為 true)。

[x \<= y](comparison-operators.md#less-than-or-equal-operator-) – 小於或等於。

[x >= y](comparison-operators.md#greater-than-or-equal-operator-) – 大於或等於。

[is](type-testing-and-conversion-operators.md#is-operator) – 型別相容性。 如果評估的左運算元可以轉換成右運算元所指定的類型，則傳回 `true`。

[as](type-testing-and-conversion-operators.md#as-operator) – 型別轉換。 傳回左運算元轉換成右運算元所指定的類型，但 `as` 會在 `(T)x` 會擲回例外狀況時傳回 `null`。

## <a name="equality-operators"></a>等號比較運算子

這些運算子具有的優先順序高於下一個區段且低於前一個區段。

[x == y](equality-operators.md#equality-operator-) – 相等。 根據預設，對於 `string` 以外的參考類型，這會傳回參考相等 (識別測試)。 不過，類型可以多載 `==`，因此如果您的目的是要測試識別，最好使用 `object` 上的 `ReferenceEquals` 方法。

[x != y](equality-operators.md#inequality-operator-) – 不等於。 請參閱 `==` 的註解。 如果類型多載 `==`，則它必須多載 `!=`。

## <a name="logical-and-operator"></a>邏輯 AND 運算子

此運算子具有的優先順序高於下一個區段且低於前一個區段。

`x & y` – `bool` 運算元的 [邏輯 AND](boolean-logical-operators.md#logical-and-operator-)，或整數型別之運算元的 [位元邏輯 AND](bitwise-and-shift-operators.md#logical-and-operator-)。

## <a name="logical-xor-operator"></a>邏輯 XOR 運算子

此運算子具有的優先順序高於下一個區段且低於前一個區段。

`x ^ y` – `bool` 運算元的 [邏輯 XOR](boolean-logical-operators.md#logical-exclusive-or-operator-)，或整數型別之運算元的 [位元邏輯 XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-)。

## <a name="logical-or-operator"></a>邏輯 OR 運算子

此運算子具有的優先順序高於下一個區段且低於前一個區段。

`x | y` – `bool` 運算元的 [邏輯 OR](boolean-logical-operators.md#logical-or-operator-)，或整數型別之運算元的 [位元邏輯 OR](bitwise-and-shift-operators.md#logical-or-operator-)。

## <a name="conditional-and-operator"></a>條件 AND 運算子

此運算子具有的優先順序高於下一個區段且低於前一個區段。

[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – 邏輯 AND。 如果 `x` 評估為 `false`，則 `y` 不會被評估。

## <a name="conditional-or-operator"></a>條件 OR 運算子

此運算子具有的優先順序高於下一個區段且低於前一個區段。

[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – 邏輯 OR。 如果 `x` 評估為 `true`，則 `y` 不會被評估。

## <a name="null-coalescing-operator"></a>Null 聯合運算子

此運算子具有的優先順序高於下一個區段且低於前一個區段。

[x ?? y](null-coalescing-operator.md) – 如果非 `null` 則傳回 `x`，否則會傳回 `y`。

## <a name="conditional-operator"></a>條件運算子

此運算子具有的優先順序高於下一個區段且低於前一個區段。

[t ? x : y](conditional-operator.md) - 如果測試 `t` 評估為 true，則會評估並傳回 `x`，否則會評估並傳回 `y`。

## <a name="assignment-and-lambda-operators"></a>指派和 Lambda 運算子

這些運算子具有的優先順序高於下一個區段且低於前一個區段。

[x = y](assignment-operator.md) – 指派。

[x += y](arithmetic-operators.md#compound-assignment) – 遞增。 將 `y` 的值加上 `x` 的值，將結果儲存在 `x`，並傳回新的值。 如果 `x` 指定 [event](../keywords/event.md)，則 `y` 必須是 C# 視為事件處理常式新增的適當方法。

[x -= y](arithmetic-operators.md#compound-assignment) – 遞減。 將 `x` 的值減去 `y` 的值，將結果儲存在 `x`，並傳回新的值。 如果 `x` 指定 [event](../keywords/event.md)，則 `y` 必須是 C# 視為事件處理常式移除的適當方法。

[x *= y](arithmetic-operators.md#compound-assignment) – 乘法指派。 將 `y` 的值乘以 `x` 的值，將結果儲存在 `x`，並傳回新的值。

[x /= y](arithmetic-operators.md#compound-assignment) – 除法指派。 將 `x` 的值除以 `y` 的值，將結果儲存在 `x`，並傳回新的值。

[x %= y](arithmetic-operators.md#compound-assignment) – 餘數指派。 將 `x` 的值除以 `y` 的值，將餘數儲存在 `x`，並傳回新的值。

[x &= y](boolean-logical-operators.md#compound-assignment) – AND 指派。 將 `y` 的值和 `x` 的值進行 AND 處理，將結果儲存在 `x`，並傳回新的值。

[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR 指派。 將 `y` 的值和 `x` 的值進行 OR 處理，將結果儲存在 `x`，並傳回新的值。

[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR 指派。 將 `y` 的值和 `x` 的值進行 XOR 處理，將結果儲存在 `x`，並傳回新的值。

[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – 左移指派。 將 `x` 的值向左移 `y` 個空格，將結果儲存在 `x`，並傳回新的值。

[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – 右移指派。 將 `x` 的值向右移 `y` 個空格，將結果儲存在 `x`，並傳回新的值。

[=>](lambda-operator.md) – lambda 宣告。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [運算子](../../programming-guide/statements-expressions-operators/operators.md)
- [多載運算子](../../programming-guide/statements-expressions-operators/overloadable-operators.md)

---
title: C# 運算子
ms.date: 04/04/2018
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
ms.openlocfilehash: f4267caeb6301950b9f6a8b9545a47b9f48e7920
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977375"
---
# <a name="c-operators"></a>C# 運算子

C# 提供許多運算子，也就是指定要在運算式中執行哪些作業 (數學、索引化、函式呼叫等) 的符號。 您可以[多載](../../programming-guide/statements-expressions-operators/overloadable-operators.md)許多運算子，以便在套用至使用者定義型別時變更它們的意義。

列舉 (`enum`) 型別上通常會允許整數型別上的作業 (例如 `==`、`!=`、`<`、`>`、`&`、`|`)。

下列區段列出 C# 運算子，從最高優先順序開始到最低優先順序。 每個區段中的運算子會共用相同的優先順序層級。

## <a name="primary-operators"></a>主要運算子

這些是最高優先順序的運算子。

[x.y](member-access-operator.md) – 成員存取。

[x?.y](null-conditional-operators.md) – null 條件成員存取。 如果左運算元評估為 `null`，則傳回 `null`。

[x?[y]](null-conditional-operators.md) - null 條件式索引存取。 如果左運算元評估為 `null`，則傳回 `null`。

[f(x)](invocation-operator.md) – 函式引動過程。

[a&#91;x&#93;](index-operator.md) – 彙總物件索引化。

[x++](arithmetic-operators.md#increment-operator-) – 後置遞增。 傳回 x 的值，然後利用大於 x 值的值 (通常會加上整數 1) 更新儲存位置。

[x--](arithmetic-operators.md#decrement-operator---) – 後置遞減。 傳回 x 的值，然後利用小於 x 值的值 (通常會減去整數 1) 更新儲存位置。

[new](../keywords/new-operator.md) – 型別執行個體化。

[typeof](../keywords/typeof.md) - 傳回代表運算元的 <xref:System.Type> 物件。

[checked](../keywords/checked.md) – 啟動整數作業的溢位檢查。

[unchecked](../keywords/unchecked.md) – 停用整數作業的溢位檢查。 這是預設編譯器行為。

[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) - 產生類型 T 的預設值。

[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – 宣告並傳回委派執行個體。

[sizeof](../keywords/sizeof.md) – 傳回型別運算元的大小 (以位元組為單位)。

[->](dereference-operator.md) – 指標取值結合成員存取。

## <a name="unary-operators"></a>一元運算子

這些運算子具有的優先順序高於下一個區段且低於前一個區段。

[+x](addition-operator.md) – 傳回 x 的值。

[-x](subtraction-operator.md) – 數值否定。

[\!x](boolean-logical-operators.md#logical-negation-operator-) – 邏輯否定。

[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – 位元補數。

[++x](arithmetic-operators.md#increment-operator-) – 前置遞增。 傳回 x 的值之前，利用大於 x 值的值 (通常會加上整數 1) 更新儲存位置。

[--x](arithmetic-operators.md#decrement-operator---) – 前置遞減。 更新儲存體位置之後，傳回 x 減一的 x 值 (通常減去整數 1)。

[(T)x](invocation-operator.md) – 型別轉換。

[await](../keywords/await.md) – 等候 `Task`。

[&x](and-operator.md) – 位址。

[*x](multiplication-operator.md) – 取值。

[true 運算子](../keywords/true-false-operators.md) - 傳回 [bool](../keywords/bool.md) 值 `true` 以指出運算元必然為 true。

[false 運算子](../keywords/true-false-operators.md) - 傳回 [bool](../keywords/bool.md) 值 `true`，以指出運算元必然為 false。

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

[x \< y](less-than-operator.md) – 小於 (如果 x 小於 y，則為 true)。

[x > y](greater-than-operator.md) – 大於 (如果 x 大於 y，則為 true)。

[x \<= y](less-than-equal-operator.md) – 小於或等於。

[x >= y](greater-than-equal-operator.md) – 大於或等於。

[is](../keywords/is.md) – 型別相容性。 如果評估的左運算元可以轉換成右運算元中指定的類型 (靜態類型)，則傳回 true。

[as](../keywords/as.md) – 型別轉換。 傳回的左運算元轉型為右運算元指定的類型 (靜態類型)，但 `as` 傳回 `null`，其中 `(T)x` 會擲回例外狀況。

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

[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – 邏輯 AND。 如果第一個運算元評估為 false，C# 就不會評估第二個運算元。

## <a name="conditional-or-operator"></a>條件 OR 運算子

此運算子具有的優先順序高於下一個區段且低於前一個區段。

[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – 邏輯 OR。 如果第一個運算元評估為 true，C# 就不會評估第二個運算元。

## <a name="null-coalescing-operator"></a>Null 聯合運算子

此運算子具有的優先順序高於下一個區段且低於前一個區段。

[x ?? y](null-coalescing-operator.md) – 如果非 `null` 則傳回 `x`，否則會傳回 `y`。

## <a name="conditional-operator"></a>條件運算子

此運算子具有的優先順序高於下一個區段且低於前一個區段。

[t ? x : y](conditional-operator.md) - 如果測試 `t` 評估為 true，則會評估並傳回 `x`，否則會評估並傳回 `y`。

## <a name="assignment-and-lambda-operators"></a>指派和 Lambda 運算子

這些運算子具有的優先順序高於下一個區段且低於前一個區段。

[x = y](assignment-operator.md) – 指派。

[x += y](addition-assignment-operator.md) – 遞增。 將 `y` 的值加上 `x` 的值，將結果儲存在 `x`，並傳回新的值。 如果 `x` 指定 `event`，則 `y` 必須是適當的函式，其中會將 C# 視為事件處理常式予以新增。

[x -= y](subtraction-assignment-operator.md) – 遞減。 將 `x` 的值減去 `y` 的值，將結果儲存在 `x`，並傳回新的值。 如果 `x` 指定 `event`，則 `y` 必須是適當的函式，其中會將 C# 視為事件處理常式予以移除。

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
- [C# 程式設計指南](../../programming-guide/index.md)
- [C#](../../index.md)
- [多載運算子](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [C# 關鍵字](../keywords/index.md)

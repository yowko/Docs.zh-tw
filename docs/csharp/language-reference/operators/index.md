---
title: "C# 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.operators"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "位址運算子 [C#]"
  - "算術運算子 [C#]"
  - "指派運算子 [C#]"
  - "位元運算子 [C#]"
  - "布林運算子 [C#]"
  - "運算式 [C#], 運算子"
  - "間接取值運算子 [C#]"
  - "關鍵字 [C#], 運算子"
  - "邏輯運算子 [C#]"
  - "運算子 [C#]"
  - "關係運算子 [C#]"
  - "移位運算子 [C#]"
  - "Visual C#, 運算子"
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
caps.latest.revision: 40
caps.handback.revision: 38
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# C# 運算子
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# 提供許多運算子，也就是指定要在運算式中執行哪些作業 \(數學、索引化、函式呼叫等\) 的符號。  您可以[多載](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)許多運算子，以便在套用至使用者定義類型時變更它們的意義。  
  
 通常允許整數類資料型別上的作業 \(例如 `==`、`!=`、`<`、`>`、`&`、                  `|` \) 出現在列舉 \(`enum`\) 類型上。  
  
 這些區段列出 C\# 運算子，從最高優先順序開始到最低優先順序。  每個區段中的運算子會共用相同的優先順序層級。  
  
## 主要運算子  
 這些是最高優先順序的運算子。  請注意，您可以按一下運算子以移至內附範例的詳細頁面。  
  
 [x.y](../../../csharp/language-reference/operators/member-access-operator.md) – 成員存取。  
  
 [x?.y](../../../csharp/language-reference/operators/null-conditional-operators.md) – null 條件成員存取。  如果左側運算元為 null，則會傳回 null。  
  
 [f\(x\)](../../../csharp/language-reference/operators/invocation-operator.md) – 函式引動過程。  
  
 [a&#91;x&#93;](../../../csharp/language-reference/operators/index-operator.md) – 彙總物件索引化。  
  
 [a?&#91;x&#93;](../../../csharp/language-reference/operators/null-conditional-operators.md) – null 條件索引化。  如果左側運算元為 null，則會傳回 null。  
  
 [x\+\+](../../../csharp/language-reference/operators/increment-operator.md) – 後置遞增。  傳回 x 的值，然後利用大於 x 值的值 \(通常會加上整數 1\) 更新儲存位置。  
  
 [x\-\-](../../../csharp/language-reference/operators/decrement-operator.md) –  後置遞減。  傳回 x 的值，然後利用小於 x 值的值 \(通常會減去整數 1\) 更新儲存位置。  
  
 [New](../../../csharp/language-reference/keywords/new-operator.md) – 類型執行個體化。  
  
 [Typeof](../../../csharp/language-reference/keywords/typeof.md) – 傳回代表運算元的 System.Type 物件。  
  
 [Checked](../../../csharp/language-reference/keywords/checked.md) – 啟動整數作業的溢位檢查。  
  
 [Unchecked](../../../csharp/language-reference/keywords/unchecked.md) – 停用整數作業的溢位檢查。  這是預設編譯器行為。  
  
 [default\(T\)](../../../csharp/programming-guide/generics/default-keyword-in-generic-code.md) – 傳回類型 T 的預設初始化值，參考類型為 null、數字類型為零，而結構類型的成員則填入零\/null。  
  
 [Delegate](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) – 宣告並傳回委派執行個體。  
  
 [Sizeof](../../../csharp/language-reference/keywords/sizeof.md) – 傳回類型運算元的大小 \(以位元組為單位\)。  
  
 [\-\>](../../../csharp/language-reference/operators/dereference-operator.md) – 指標取值結合成員存取。  
  
## 一元運算子  
 這些運算子具有的優先順序高於下一個區段且低於前一個區段。  請注意，您可以按一下運算子以移至內附範例的詳細頁面。  
  
 [\+x](../../../csharp/language-reference/operators/addition-operator.md) – 傳回 x 的值。  
  
 [\-x](../../../csharp/language-reference/operators/subtraction-operator.md) – 數值否定。  
  
 [\!x](../../../csharp/language-reference/operators/logical-negation-operator.md) – 邏輯否定。  
  
 [~x](../../../csharp/language-reference/operators/bitwise-complement-operator.md) – 位元補數。  
  
 [\+\+x](../../../csharp/language-reference/operators/increment-operator.md) – 前置遞增。  傳回 x 的值之前，利用大於 x 值的值 \(通常會加上整數 1\) 更新儲存位置。  
  
 [\-\-x](../../../csharp/language-reference/operators/decrement-operator.md) – 前置遞減。  傳回 x 的值之前，利用小於 x 值的值 \(通常會加上整數 1\) 更新儲存位置。  
  
 [\(T\)x](../../../csharp/language-reference/operators/invocation-operator.md) – 類型轉換。  
  
 [Await](../../../csharp/language-reference/keywords/await.md) – 等候 `Task`。  
  
 [&x](../../../csharp/language-reference/operators/and-operator.md) – 位址。  
  
 [\*x](../../../csharp/language-reference/operators/multiplication-operator.md) – 取值。  
  
## 乘法類運算子  
 這些運算子具有的優先順序高於下一個區段且低於前一個區段。  請注意，您可以按一下運算子以移至內附範例的詳細頁面。  
  
 [x \* y](../../../csharp/language-reference/operators/multiplication-operator.md) – 乘法。  
  
 [x \/ y](../../../csharp/language-reference/operators/division-operator.md) – 除法。  如果運算元都是整數，則結果會截斷趨近於零的整數 \(例如，`-7 / 2 is -3`\)。  
  
 [x % y](../../../csharp/language-reference/operators/modulus-operator.md) – 模數。  如果運算元都是整數，這會傳回 x 除以 y 的餘數。  若為 `q = x / y` 和 `r = x % y`，則為 `x = q * y + r`。  
  
## 加法類運算子  
 這些運算子具有的優先順序高於下一個區段且低於前一個區段。  請注意，您可以按一下運算子以移至內附範例的詳細頁面。  
  
 [x \+ y](../../../csharp/language-reference/operators/addition-operator.md) – 加法。  
  
 [x – y](../../../csharp/language-reference/operators/subtraction-operator.md) – 減法。  
  
## 移位運算子  
 這些運算子具有的優先順序高於下一個區段且低於前一個區段。  請注意，您可以按一下運算子以移至內附範例的詳細頁面。  
  
 [x \<\< y](../Topic/%3C%3C%20Operator%20\(C%23%20Reference\).md) – 位元向左移位並使用右邊的零填滿。  
  
 [x \>\> y](../../../csharp/language-reference/operators/right-shift-operator.md) – 位元向右移位。  如果左運算元是 `int` 或 `long`，則以正負號位元填入左位元。  如果左運算元是 `uint` 或 `ulong`，則以零填入左位元。  
  
## 關係和類型測試運算子  
 這些運算子具有的優先順序高於下一個區段且低於前一個區段。  請注意，您可以按一下運算子以移至內附範例的詳細頁面。  
  
 [x \< y](../../../csharp/language-reference/operators/less-than-operator.md) – 小於 \(如果 x 小於 y，則為 true\)。  
  
 [x \> y](../../../csharp/language-reference/operators/greater-than-operator.md) – 大於 \(如果 x 大於 y，則為 true\)。  
  
 [x \< \= y](../../../csharp/language-reference/operators/less-than-equal-operator.md) – 小於或等於。  
  
 [x \> \= y](../../../csharp/language-reference/operators/greater-than-equal-operator.md) – 小於或等於。  
  
 [Is](../../../csharp/language-reference/keywords/is.md) – 類型相容性。  如果評估的左運算元可以轉換成右運算元中指定的類型 \(靜態類型\)，則傳回 true。  
  
 [As](../../../csharp/language-reference/keywords/as.md) – 類型轉換。  傳回的左運算元轉型為右運算元指定的類型 \(靜態類型\)，但 `as` 傳回 `null`，其中 `(T)x` 會擲回例外狀況。  
  
## 等號比較運算子  
 這些運算子具有的優先順序高於下一個區段且低於前一個區段。  請注意，您可以按一下運算子以移至內附範例的詳細頁面。  
  
 [x \=\= y](../../../csharp/language-reference/operators/equality-comparison-operator.md) – 相等。  根據預設，對於 `string` 以外的參考類型，這會傳回參考相等 \(識別測試\)。  不過，類型可以多載 `==`，因此如果您的目的是要測試識別，最好使用 `object` 上的 `ReferenceEquals` 方法。  
  
 [x \!\= y](../../../csharp/language-reference/operators/not-equal-operator.md) – 不等於。  請參閱 `==` 的註解。  如果類型多載 `==`，則它必須多載 `!=`。  
  
## 邏輯 AND 運算子  
 此運算子具有的優先順序高於下一個區段且低於前一個區段。  請注意，您可以按一下運算子以移至內附範例的詳細資料頁面。  
  
 [x & y](../../../csharp/language-reference/operators/and-operator.md) – 邏輯或位元 AND。  通常允許將整數類型和 `enum` 類型搭配使用。  
  
## 邏輯 XOR 運算子  
 此運算子具有的優先順序高於下一個區段且低於前一個區段。  請注意，您可以按一下運算子以移至內附範例的詳細資料頁面。  
  
 [x ^ y](../../../csharp/language-reference/operators/xor-operator.md) – 邏輯或位元 XOR。  您通常可以將整數類型和 `enum` 類型搭配使用。  
  
## 邏輯 OR 運算子  
 此運算子具有的優先順序高於下一個區段且低於前一個區段。  請注意，您可以按一下運算子以移至內附範例的詳細資料頁面。  
  
 [x &#124; y](../../../csharp/language-reference/operators/or-operator.md) – 邏輯或位元 OR。  通常允許將整數類型和 `enum` 類型搭配使用。  
  
## 條件 AND 運算子  
 此運算子具有的優先順序高於下一個區段且低於前一個區段。  請注意，您可以按一下運算子以移至內附範例的詳細資料頁面。  
  
 [x && y](../../../csharp/language-reference/operators/conditional-and-operator.md) – 邏輯 AND。  如果第一個運算元為 false，C\# 就不會評估第二個運算元。  
  
## 條件 OR 運算子  
 此運算子具有的優先順序高於下一個區段且低於前一個區段。  請注意，您可以按一下運算子以移至內附範例的詳細資料頁面。  
  
 [x &#124;&#124; y](../Topic/%7C%7C%20Operator%20\(C%23%20Reference\).md) – 邏輯 OR。  如果第一個運算元為 true，C\# 就不會評估第二個運算元。  
  
## Null 聯合運算子  
 此運算子具有的優先順序高於下一個區段且低於前一個區段。  請注意，您可以按一下運算子以移至內附範例的詳細資料頁面。  
  
 [x ?? y](../../../csharp/language-reference/operators/null-conditional-operator.md) – 如果非 `null` 則傳回 `x`，否則會傳回 `y`。  
  
## 條件運算子  
 此運算子具有的優先順序高於下一個區段且低於前一個區段。  請注意，您可以按一下運算子以移至內附範例的詳細資料頁面。  
  
 [t ? x : y](../Topic/?:%20Operator%20\(C%23%20Reference\).md) – 如果測試 `t` 為 true，則會評估並傳回 `x`，否則會評估並傳回 `y`。  
  
## 指派和 Lambda 運算子  
 這些運算子具有的優先順序高於下一個區段且低於前一個區段。  請注意，您可以按一下運算子以移至內附範例的詳細頁面。  
  
 [x \= y](../../../csharp/language-reference/operators/assignment-operator.md) – 指派。  
  
 [x \+\= y](../../../csharp/language-reference/operators/addition-assignment-operator.md) – 遞增。  將 `y` 的值加上 `x` 的值，將結果儲存在 `x`，並傳回新的值。  如果 `x` 指定 `event`，則 `y` 必須是適當的函式，其中會將 C\# 視為事件處理常式予以新增。  
  
 [x \-\= y](../../../csharp/language-reference/operators/subtraction-assignment-operator-1.md) – 遞減。  將 `x` 的值減去 `y` 的值，將結果儲存在 `x`，並傳回新的值。  如果 `x` 指定 `event`，則 `y` 必須是適當的函式，其中會將 C\# 視為事件處理常式予以移除。  
  
 [x \*\= y](../../../csharp/language-reference/operators/multiplication-assignment-operator.md) – 乘法指派。  將 `y` 的值乘以 `x` 的值，將結果儲存在 `x`，並傳回新的值。  
  
 [x \/\= y](../../../csharp/language-reference/operators/subtraction-assignment-operator.md) – 除法指派。  將 `x` 的值除以 `y` 的值，將結果儲存在 `x`，並傳回新的值。  
  
 [x %\= y](../../../csharp/language-reference/operators/modulus-assignment-operator.md) – 模數指派。  將 `x` 的值除以 `y` 的值，將餘數儲存在 `x`，並傳回新的值。  
  
 [x &\= y](../../../visual-basic/language-reference/operators/and-assignment-operator.md) – AND 指派。  將 `y` 的值和 `x` 的值進行 AND 處理，將結果儲存在 `x`，並傳回新的值。  
  
 [x &#124;\= y](../../../csharp/language-reference/operators/or-assignment-operator.md) – OR 指派。  將 `y` 的值和 `x` 的值進行 OR 處理，將結果儲存在 `x`，並傳回新的值。  
  
 [x ^\= y](../../../csharp/language-reference/operators/xor-assignment-operator.md) – XOR 指派。  將 `y` 的值和 `x` 的值進行 XOR 處理，將結果儲存在 `x`，並傳回新的值。  
  
 [x \<\<\= y](../../../csharp/language-reference/operators/left-shift-assignment-operator.md) – 左移指派。  將 `x` 的值向左移 `y` 個空格，將結果儲存在 `x`，並傳回新的值。  
  
 [x \>\>\= y](../../../csharp/language-reference/operators/right-shift-assignment-operator.md) – 右移指派。  將 `x` 的值向右移 `y` 個空格，將結果儲存在 `x`，並傳回新的值。  
  
 [\=\>](../../../csharp/language-reference/operators/lambda-operator.md) – lambda 宣告。  
  
## 算術溢位  
 算術運算子 \([\+](../../../csharp/language-reference/operators/addition-operator.md)、[\-](../../../csharp/language-reference/operators/subtraction-operator.md)、[\*](../../../csharp/language-reference/operators/multiplication-operator.md)、[\/](../../../csharp/language-reference/operators/division-operator.md)\) 可產生數值類型所涉及之可能值範圍以外的結果。  您應該參考特定運算子一節以取得詳細資料，但一般而言：  
  
-   整數算術溢位可能會擲回 <xref:System.OverflowException> 或捨棄結果的最高有效位元。  整數除以零一定會擲回 `DivideByZeroException`。  
  
-   浮點算術溢位或除以零永遠不會擲回例外狀況，因為浮點類型以 IEEE 754 為基礎，所以具有代表無限與 NaN \(而非數字\) 的佈建。  
  
-   [十進位](../../../csharp/language-reference/keywords/decimal.md)算術溢位一定會擲回 <xref:System.OverflowException>。  十進位除以零一定會擲回 <xref:System.DivideByZeroException>。  
  
 發生整數溢位時，會發生的事取決於執行內容，可以是 [checked 或 unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)。  在 checked 內容中，會擲回 <xref:System.OverflowException>。  在 unchecked 內容中，會捨棄結果的最高有效位元並繼續執行。  因此，C\# 可讓您選擇處理或忽略溢位。  
  
 除了算術運算子之外，整數類資料類型至整數類資料類型的轉換可能會造成溢位，例如，[long](../../../csharp/language-reference/keywords/long.md) 轉換為 [int](../../../csharp/language-reference/keywords/int.md)，且有可能受 checked 或 unchecked 執行的限制。  不過，位元運算子和移位運算子永遠不會造成溢位。  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\#](../../../csharp/csharp.md)   
 [多載運算子](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)
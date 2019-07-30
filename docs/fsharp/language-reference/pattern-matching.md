---
title: 模式比對
description: 瞭解如何在中F#使用模式來比較資料與邏輯結構、將資料分解成組成元件, 或從資料中提取資訊。
ms.date: 05/16/2016
ms.openlocfilehash: 156bb670e0c494a3d515eab03e2e4672d6743dec
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627293"
---
# <a name="pattern-matching"></a>模式比對

模式是轉換輸入資料的規則。 這兩種方法都F#是用來比較資料與邏輯結構或結構、將資料分解成組成元件, 或從資料中以各種方式來解壓縮資訊。

## <a name="remarks"></a>備註

模式用於許多語言結構, 例如`match`運算式。 當您要在`let`系結、lambda 運算式和`try...with`與運算式相關聯的例外狀況處理常式中處理函式的引數時, 會使用這些函數。 如需詳細資訊, 請參閱[Match 運算式](match-expressions.md)、 [let](./functions/let-bindings.md)系結、 [Lambda 運算式:`fun` 關鍵字](./functions/lambda-expressions-the-fun-keyword.md)和例外[狀況:`try...with`運算式。](/.exception-handling/the-try-with-expression.md)

例如, 在`match`運算式中,*模式*就是管道符號後面的內容。

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

每個模式都是以某種方式轉換輸入的規則。 `match`在運算式中, 會接著檢查每個模式, 以查看輸入資料是否與模式相容。 如果找到相符的, 則會執行結果運算式。 如果找不到相符的, 則會測試下一個模式規則。 [Match 運算式](match-expressions.md)中說明了*條件*部分時的選擇性時機。

下表顯示支援的模式。 在執行時間, 系統會依照表格中所列的順序, 針對下列每個模式測試輸入, 並以遞迴方式套用模式, 從第一次到最後, 和出現在您的程式碼中, 以及從左至右套用到每一行上的模式。

|名稱|描述|範例|
|----|-----------|-------|
|常數模式|任何數值、字元或字串常值、列舉常數或定義的常值識別碼|`1.0`, `"test"`, `30`, `Color.Red`|
|識別碼模式|區分聯集、例外狀況標籤或作用中模式案例的大小寫值|`Some(x)`<br /><br />`Failure(msg)`|
|變數模式|*identifier*|`a`|
|`as`pattern|*模式*作為*識別碼*|`(a, b) as tuple1`|
|OR 模式|*pattern1* &#124; *pattern2*|<code>([h] &#124; [h; _])</code>|
|AND 模式|*pattern1* &amp; *pattern2*|`(a, b) & (_, "test")`|
|缺點模式|*identifier* :: *list-identifier*|`h :: t`|
|清單模式|[ *pattern_1*; ... ; *pattern_n* ]|`[ a; b; c ]`|
|陣列模式|[&#124; *pattern_1*; ...;*pattern_n*&#124;]|<code>[&#124; a; b; c &#124;]</code>|
|以括弧括住的模式|(*模式*)|`( a )`|
|元組模式|( *pattern_1*, ..., *pattern_n* )|`( a, b )`|
|記錄模式|{ *identifier1*  =  *pattern_1*; ...;*identifier_n* =  *pattern_n* }|`{ Name = name; }`|
|萬用字元模式|_|`_`|
|搭配類型注釋的模式|*模式*:*類型*|`a : int`|
|類型測試模式|:? *類型*[as *identifier* ]|`:? System.DateTime as dt`|
|Null 模式|null|`null`|

## <a name="constant-patterns"></a>常數模式

常數模式是數值、字元和字串常值、列舉常數 (包含列舉型別名稱)。 只有常數模式的運算式可以與其他語言中的case語句進行比較。`match` 輸入會與常值進行比較, 而如果值相等, 則會符合模式。 常值的型別必須與輸入的型別相容。

下列範例示範如何使用常值模式, 而且也會使用變數模式和或模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

常值模式的另一個範例是以列舉常數為基礎的模式。 當您使用列舉常數時, 必須指定列舉類型名稱。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>識別碼模式

如果模式是形成有效識別碼的字元字串, 則識別碼的格式會決定模式的比對方式。 如果識別碼長度超過單一字元, 並以大寫字元開頭, 則編譯器會嘗試對識別碼模式進行比對。 此模式的識別碼可以是以 Literal 屬性、區分聯集大小寫、例外狀況識別碼或作用中模式案例標記的值。 如果找不到相符的識別碼, 比對會失敗, 而下一個模式規則 (變數模式) 則會與輸入進行比較。

區分聯集模式可以是簡單的命名案例, 或者可以有值, 或包含多個值的元組。 如果有值, 您必須指定值的識別碼。 在元組的情況下, 您必須為元組的每個專案提供一個識別碼, 或為一個或多個命名聯集欄位指定具有功能變數名稱的識別碼。 如需範例, 請參閱本節中的程式碼範例。

此`option`類型是有兩個`Some`案例的區分聯集: `None`和。 其中一個案例`Some`() 具有值, 但另一個 (`None`) 只是一個名為的大小寫。 因此, `Some` `Some`與案例相關聯的值需要有變數, 但`None`必須單獨顯示。 在下列程式碼中, 會`var1`提供變數比`Some`對案例所取得的值。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

在下列範例中, `PersonName` 「區分聯集」包含字串和字元的混合, 表示可能的名稱形式。 區分聯集的案例為`FirstOnly`、 `LastOnly`和`FirstLast`。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

針對具有命名欄位的區分等位, 您可以使用等號 (=) 來解壓縮已命名欄位的值。 例如, 請考慮具有類似下列宣告的區分聯集。

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

您可以使用模式比對運算式中的已命名欄位, 如下所示。

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

使用命名欄位是選擇性的, 因此在前一個範例中, 和`Circle(r)` `Circle(radius = r)`都具有相同的效果。

當您指定多個欄位時, 請使用分號 (;)作為分隔符號。

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

現用模式可讓您定義更複雜的自訂模式比對。 如需現用模式的詳細資訊, 請參閱[現用模式](active-patterns.md)。

在例外狀況處理常式內容中的模式比對中, 會使用識別碼為例外狀況的情況。 如需例外狀況處理中的模式比對[的詳細資訊, 請參閱例外狀況:`try...with`運算式。](/.exception-handling/the-try-with-expression.md)

## <a name="variable-patterns"></a>變數模式

變數模式會指派符合變數名稱的值, 然後可以在`->`符號右邊的執行運算式中使用。 變數模式本身會符合任何輸入, 但變數模式通常會出現在其他模式中, 因此可讓更複雜的結構 (例如元組和陣列) 分解為變數。

下列範例示範在元組模式內的變數模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>as 模式

模式是一個`as`已附加子句的模式。 `as` 子句會將相符的值系結至可在`match`運算式的執行運算式中使用的名稱, 或者, 如果在系結中`let`使用此模式, 則會將名稱當做系結加入至本機範圍。 `as`

下列範例會使用`as`模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>OR 模式

當輸入資料可以符合多個模式, 而您想要執行與結果相同的程式碼時, 就會使用或模式。 或模式的兩邊類型都必須相容。

下列範例示範或模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>AND 模式

和模式需要輸入符合兩個模式。 和模式的兩邊類型都必須相容。

下列範例如`detectZeroTuple`本主題稍後的「[元組模式](https://msdn.microsoft.com/library/#tuple)」一節所示`var1` , 但在此, 我們會使用和模式, 將和`var2`都當做值來取得。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>缺點模式

缺點模式是用來將清單分解成第一個專案、*標頭*, 以及包含其餘元素的清單 (*結尾*)。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>清單模式

清單模式可讓清單分解成數個元素。 清單模式本身只能符合特定專案數目的清單。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>陣列模式

陣列模式類似于清單模式, 可以用來分解特定長度的陣列。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>以括弧括住的模式

括弧可以根據模式分組, 以達到所需的關聯性。 在下列範例中, 括弧是用來控制 AND 模式與缺點模式之間的關聯性。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>元組模式

元組模式會比對元組形式的輸入, 並透過針對元組中的每個位置使用模式比對變數, 讓元組分解成其組成元素。

下列範例示範元組模式, 同時使用常值模式、變數模式和萬用字元模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>記錄模式

記錄模式可用來分解記錄, 以將欄位的值解壓縮。 模式不需要參考記錄的所有欄位;任何省略的欄位都不會參與比對, 也不會被解壓縮。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>萬用字元模式

萬用字元模式是以底線 (`_`) 字元表示並比對任何輸入, 就像變數模式一樣, 不同的是會捨棄輸入, 而不是指派給變數。 萬用字元模式通常用於其他模式中, 做為`->`符號右邊運算式中不需要的值預留位置。 萬用字元模式也經常用於模式清單的結尾, 以符合任何不相符的輸入。 本主題的許多程式碼範例會示範萬用字元模式。 如需其中一個範例, 請參閱上述程式碼。

## <a name="patterns-that-have-type-annotations"></a>具有類型注釋的模式

模式可以具有類型注釋。 這些行為與其他類型注釋和指南推斷類似, 如同其他類型注釋。 模式中的類型注釋前後需要括弧。 下列程式碼顯示具有類型注釋的模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>類型測試模式

類型測試模式是用來比對輸入與類型。 如果輸入類型與模式中指定的類型相符 (或衍生的類型), 則比對成功。

下列範例示範型別測試模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a>Null 模式

Null 模式符合當您使用允許 null 值的類型時, 可能會出現的 null 值。 當與 .NET Framework 的程式碼互通時, 經常會使用 Null 模式。 例如, .net API 的傳回值可能是`match`運算式的輸入。 您可以根據傳回值是否為 null, 以及所傳回值的其他特性, 來控制程式流程。 您可以使用 null 模式來防止 null 值傳播到程式的其餘部分。

下列範例會使用 null 模式和變數模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>另請參閱

- [比對運算式](match-expressions.md)
- [使用中模式](active-patterns.md)
- [F# 語言參考](index.md)

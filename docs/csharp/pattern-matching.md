---
title: 模式比對 - C# 手冊
description: 了解 C# 中的模式比對運算式
ms.date: 01/24/2017
ms.assetid: 1e575c32-2e2b-4425-9dca-7d118f3ed15b
ms.openlocfilehash: 635ab45c89a38f3dedac2d60ea1e31ebf394c9b2
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231472"
---
# <a name="pattern-matching"></a>模式比對 #

模式可測試某值是否具有特定的「圖形」，而且當該值有符合的圖形時，可從該值「擷取」資訊。 模式比對會提供更簡潔的語法提供目前所用的演算法使用。 您已使用現有的語法建立模式比對演算法。 您撰寫 `if` 或 `switch` 陳述式測試值。 然後，當這些陳述式符合時，使用從該值擷取的資訊。 新的語法項目是您已熟悉的陳述式延伸模組︰`is` 和 `switch`。 這些新的延伸模組結合測試值及擷取該資訊。

在本主題中，我們會探討新的語法，告訴您它如何讓程式碼易讀又簡潔。 模式比對可使用資料和程式碼分隔的慣用句，不像物件取向的設計，資料和操作資料的方法是緊密結合的。

為說明這些新的慣用句，讓我們使用模式比對陳述式來處理表示幾何圖形的結構。 您可能熟悉以物件的執行階段型別為基礎，建置類別階層架構以及建立[虛擬方法和覆寫方法](methods.md#inherited)來自訂物件行為。

這些技術不是用來處理非以類別階層結構化的資料。 當資料和方法分開時，您需要其他工具。 新的「模式比對」建構能用更簡潔的語法來檢視資料，並根據該資料的任何條件來管理控制流程。 您已經撰寫測試變數值的 `if` 陳述式和 `switch`。 您撰寫了測試變數類型的 `is` 陳述式。 「模式比對」將新功能加 入這些陳述式。

在本主題中，您會建置一種方法，計算不同幾何圖形的面積。 但是，您在執行作業時不必訴諸物件導向技術，也不用建置不同圖形的類別階層。
您要改用「模式比對」。 為進一步強調我們不使用繼承，您需要將每個圖形變成 `struct` 而非類別。 請注意，不同的 `struct` 型別不能指定一般使用者定義的基底型別，因此繼承不是可行的設計。
當您瀏覽此範例時，請將此程式碼與它如何結構化為物件階層進行對比。 當您必須查詢及操作的資料不是類別階層時，模式比對可使用非常簡潔的設計。

不是從抽象圖形定義與加入不同的特定圖形類別開始，讓我們改從只定義每個幾何圖形的簡單資料開始︰

[!code-csharp[ShapeDefinitions](../../samples/csharp/PatternMatching/Shapes.cs#01_ShapeDefinitions "Shape definitions")]

讓我們從這些結構撰寫方法，計算某些圖形的面積。

## <a name="the-is-type-pattern-expression"></a>`is` 型別模式運算式

在 C# 7.0 之前，您需要以一系列的 `if` 和 `is` 陳述式測試每個型別：

[!code-csharp[ClassicIsExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#02_ClassicIsExpression "Classic type pattern using is")]

上述程式碼是「型別模式」的傳統運算式︰您要測試變數，以判斷其型別並根據該型別採取不同的動作。

如果測試成功，使用 `is` 運算式的延伸模組來指派變數，此程式碼會變得更簡單：

[!code-csharp[IsPatternExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#03_IsPatternExpression "is pattern expression")]

在此更新的版本中，`is` 運算式會測試變數並將它指派給適當型別的新變數。 另請注意，此版本包含 `Rectangle` 型別，它是 `struct`。 新的 `is` 運算式可搭配實值型別以及參考型別。

模式比對運算式的語言規則可協助您避免誤用比對運算式的結果。 在上例中，當個別的模式比對運算式有 `true` 結果時，變數 `s`、`c` 和 `r` 只能在範圍內且要確實指派。 如果您嘗試在另一個位置使用任一變數，您的程式碼就會產生編譯器錯誤。

讓我們仔細檢查這兩項規則，就從範圍開始。 變數 `c` 只有在第一個 `if` 陳述式的 `else` 分支中時才在範圍內。 `s` 變數位於 `ComputeAreaModernIs` 方法的範圍中。 這是因為 `if` 陳述式的每個分支都會建立變數的個別範圍。 不過，`if` 陳述式本身並不會。 這表示在 `if` 陳述式中宣告的變數和 `if` 陳述式 (本例中的方法) 是在相同範圍中。此行為不是針對模式比對，但卻是變數範圍以及 `if` 和 `else` 陳述式的定義行為。

當個別的 `if` 陳述式為 true 時會指派變數 `c` 和 `s`，因為 true 機制時會明確指派。

> [!TIP]
> 本主題中的範例使用建議的建構，其模式比對 `is` 運算式會在 `if` 陳述式的 `true` 分支中明確指派比對變數。
> 您可以說明只在 `false` 分支中明確指派 `if (!(shape is Square s))` 和變數 `s`，以回復邏輯。 雖然這是有效的 C#，但不建議，因為遵循邏輯會更令人困惑。

這些規則表示您不太可能在不符合此模式時，不小心存取模式比對運算式的結果。

## <a name="using-pattern-matching-switch-statements"></a>使用模式比對 `switch` 陳述式

日積月累下，您可能需要支援其他的圖形類型。 隨著要測試的條件數目增長，您會發現使用 `is` 模式比對運算式會變得很麻煩。 除了每個要檢查的型別都需要 `if` 陳述式，如果輸入符合某單一型別，`is` 運算式還會限於測試。 在此情況下，您會發現 `switch` 模式比對運算式會是較好的選擇。 

傳統 `switch` 陳述式以前是模式運算式︰它支援常數模式。
您可以比較變數和 `case` 陳述式使用的常數︰

[!code-csharp[ClassicSwitch](../../samples/csharp/PatternMatching/GeometricUtilities.cs#04_ClassicSwitch "Classic switch statement")]

`switch` 陳述式以前支援的唯一模式是常數模式。 以前更限制為數值型別和 `string` 型別。
這些限制現已移除，而且您可以使用型別模式撰寫 `switch` 陳述式︰

[!code-csharp[Switch Type Pattern](../../samples/csharp/PatternMatching/GeometricUtilities.cs#05_SwitchTypePattern "Compute with `switch` expression")]

模式比對 `switch` 陳述式使用開發人員熟悉的語法，而開發人員之前使用傳統的 C 樣式 `switch` 陳述式。 已評估每個 `case`，且執行符合輸入變數的條件下程式碼。 程式碼無法從一個 case 運算式「繼續」執行到下一個，`case` 陳述式的語法需要每個 `case` 以 `break`、`return` 或 `goto` 結束。

> [!NOTE]
> 用來跳至另一個標籤的 `goto` 陳述式僅針對常數模式 (即傳統的 switch 陳述式) 有效。

具有控管 `switch` 陳述式的新重要規則。 `switch` 運算式已移除變數型別限制。
可使用任何型別，例如本例的 `object`。 Case 運算式不再限於常數值。 移除該限制表示重新排列 `switch` 區段可能會變更程式的行為。

當限於常數值時，只會有一個 `case` 標籤符合 `switch` 運算式的值。 給合每一個 `switch` 區段絕不繼續到下個區段的規則，它跟著的 `switch` 區段可能會以任何順序重新排列，但不影響行為。
現在，使用更一般化的 `switch` 運算式，順序對每個區段都很重要。 `switch` 運算式會以文字順序進行評估。 執行會傳送至符合 `switch` 運算式的第一個 `switch` 標籤。  
請注意，只有無任何其他狀況標籤符合時才會執行 `default` 狀況。 無論其文字順序為何，`default` 狀況都是最後才評估。 如果沒有任何 `default` 狀況，且無其他 `case` 陳述式相符，就繼續執行 `switch` 陳述式後面的陳述式。 不執行任何 `case` 標籤程式碼。

## <a name="when-clauses-in-case-expressions"></a>`case` 運算式中的 `when` 子句

對 `case` 標籤使用 `when` 子句，可為面積為 0 的圖形建立特殊案例。 邊長為 0 的正方形或半徑為 0 的圓形，面積皆為 0。 您可以對 `case` 標籤使用 `when` 子句來指定該條件︰  

[!code-csharp[ComputeDegenerateShapes](../../samples/csharp/PatternMatching/GeometricUtilities.cs#07_ComputeDegenerateShapes "Compute shapes with 0 area")]

這項變更會示範新語法的幾個重點。 首先，多個 `case` 標籤可以套用到一個 `switch` 區段。 當這些標籤的任何一個為 `true` 時，會執行陳述式區塊。 在此情況下，如果 `switch` 運算式是面積為 0 的圓形或正方形，則方法會傳回常數 0。

本例介紹第一個 `switch` 區塊中，兩個 `case` 標籤中的兩個不同變數。 請注意，`switch` 區塊中的陳述式不使用變數 `c` (圓形) 或 `s` (正方形)。
這些變數都不會明確指派在這個 `switch` 區塊中。
如果符合任一種狀況，顯然指派了其中一個變數。
不過，在編譯時期不可能分辨「哪個」已指派，因為在執行階段任何一種情況都可能符合。 因此，大多數時候當您在同一個區塊使用多個 `case` 標籤時，您不會在 `case` 陳述式中引入新的變數，或只會在 `when` 子句中使用變數。

新增這些面積為 0 的圖形後，讓我們再新增幾個圖形型別︰矩形和三角形︰

[!code-csharp[AddRectangleAndTriangle](../../samples/csharp/PatternMatching/GeometricUtilities.cs#09_AddRectangleAndTriangle "Add rectangle and triangle")]

 這組變更會新增退化狀況的 `case` 標籤，以及每個新圖形的標籤和區塊。 

最後，您可以新增 `null` 狀況，以確保引數不是 `null`：

[!code-csharp[NullCase](../../samples/csharp/PatternMatching/GeometricUtilities.cs#10_NullCase "Add null case")]

`null` 模式的特殊行為很有趣，因為模式中的常數 `null` 沒有類型，但可以轉換成任何參考型別或可為 Null 的類型。 不論變數的編譯時間類型為何，語言都會定義 `null` 值將不符合任何類型模式，而不是將 `null` 轉換為任何類型。 此行為可讓以 `switch` 為基礎的新類型模式與 `is` 陳述式一致：要檢查的值是 `null` 時，`is` 陳述式一律會傳回 `false`。 它也較為簡單：在您檢查類型之後，就不需要額外的 Null 檢查。 您可以從上述範例的任何案例區塊中不會進行任何 Null 檢查的事實得知：因為比對類型模式保證非 Null 值，所以它們不是必要的。

## <a name="var-declarations-in-case-expressions"></a>`case` 運算式中的 `var` 宣告

導入 `var` 作為比對運算式之一，為模式比對導入了一些新規則。

第一個規則是 `var` 宣告遵循正常的類型推斷規則：該類型被推斷為 switch 運算式的靜態類型。 根據該規則，類型永遠符合。

第二個規則是 `var` 宣告不具有其他類型模式運算式所包含的 null 檢查。 這表示變數可能是 null，並且在這種情況下需要 null 檢查。

這兩個規則表示在許多情況下，`case` 運算式中的 `var` 宣告與 `default` 運算式的條件相同。
因為任何非預設的案例優先於 `default` 案例，所以 `default` 案例將永遠不會執行。

> [!NOTE]
> 在已寫入 `default` 案例但永遠不會執行的案例中，編譯器不會發出警告。 這與目前列出所有可能情況的 `switch` 陳述式行為一致。

第三個規則介紹了 `var` 案例可能會很有用的使用方式。 假設您在進行模式比對，而其輸入為字串，且您要搜尋已知的命令值。 您可能會撰寫類似：

[!code-csharp[VarCaseExpression](../../samples/csharp/PatternMatching/Program.cs#VarCaseExpression "use a var case expression to filter white space")]

`var` 案例符合 `null`、空字串或任何僅包含空格的字串。 請注意，上述程式碼會使用 `?.` 運算子來確保它不會意外地擲回 <xref:System.NullReferenceException>。 `default` 案例會處理此命令剖析器無法理解的任何其他字串值。

這是一個範例，其中您可能想要考慮與 `default` 運算式不同的 `var` Case 運算式。

## <a name="conclusions"></a>結論

「模式比對建構」可讓您輕鬆管理不依繼承階層而關聯之不同變數和型別的控制流程。 您也可以控制邏輯，在變數上使用任何測試條件。 在您建置分散程度更高的應用程式時，即資料和操作資料的方法是分開的，它可讓您使用最常用的模式和慣用句。 您會發現本例使用的圖形結構不包含任何方法，只有唯讀屬性。
模式比對適用於任何資料型別。 您會撰寫檢查物件的運算式，並根據這些條件決定控制流程。

比較此範例的程式碼與遵循建立抽象 `Shape` 類別階層的設計，以及各有其虛擬方法以實作計算面積的特定衍生圖形。 當您要處理資料，而且想要分別考量資料儲存和行為時，您會經常發現模式比對運算式是非常有用的工具。


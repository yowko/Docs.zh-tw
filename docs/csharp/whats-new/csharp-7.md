---
title: C# 7 的新功能 - C# 指南
description: 取得 C# 語言未來版本 7 的新功能概觀。
keywords: C#, .NET, .NET Core, 最新功能, 新功能
author: BillWagner
ms.author: wiwagn
ms.date: 12/21/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 374ac9917464a7e83566440abab10eda8a9c8683
ms.sourcegitcommit: 32172ca05d5dcce7ef3d327b9c8639c736e0fe2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2018
---
# <a name="whats-new-in-c-7"></a>C# 7 的新功能

C# 7 新增許多新功能至 C# 語言︰
* [`out` 變數](#out-variables)
    - 您可以宣告 `out` 內嵌值作為使用它們之方法的引數。
* [Tuple](#tuples)
    - 您可以建立包含多個公用欄位的輕量、未具名的類型。 編譯器和 IDE 工具了解這些類型的語意。
* [Discard](#discards) 變數
    - Discard 是種僅能用於寫入的暫時性變數，當您不在意指派的值時，便能在指派中使用。 在解構 Tuple 及使用者定義型別，以及使用 `out` 參數呼叫方法時，Discard 變數特別實用。
* [模式比對](#pattern-matching)
    - 您可以建立以任意類型和這些類型成員的值為基礎的分支邏輯。
* [`ref` 區域變數和傳回](#ref-locals-and-returns)
    - 方法引數和區域變數可以是其他儲存體的參考。
* [區域函式](#local-functions)
    - 您可以將函式巢狀放置在其他函式內，限制其範圍和可視性。
* [更多運算式主體成員](#more-expression-bodied-members)
    - 可以使用運算式來撰寫的成員清單已經增長。
* [`throw`運算式](#throw-expressions)
    - 您可以在程式碼建構中擲回先前因為 `throw` 是陳述式而不允許的例外狀況。 
* [通用的非同步傳回型別](#generalized-async-return-types)
    - 使用 `async` 修飾詞宣告的方法除了 `Task` 和 `Task<T>` 之外，也能傳回其他類型。
* [數值常值語法增強功能](#numeric-literal-syntax-improvements)
    - 新的語彙基元改善了數值常數的可讀性。

本主題的其餘部分將討論每項功能。 您將了解每項功能背後的原因。 您將了解語法。 您會看到一些範例案例，其中使用新的功能可讓身為開發人員的您提高生產力。 

## <a name="out-variables"></a>`out` 變數

在這個版本中，支援 `out` 參數的現有語法已經過改善。  

過去，您需要將 out 變數和其初始化的宣告分為兩個不同的陳述式︰

[!code-csharp[OutVariableOldStyle](../../../samples/snippets/csharp/new-in-7/program.cs#03_OutVariableOldStyle "classic out variable declaration")]

您現在可以在方法呼叫的引數清單中宣告 `out` 變數，而不是撰寫個別的宣告陳述式︰

[!code-csharp[OutVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#01_OutVariableDeclarations "Out variable declarations")]

為了清楚起見，您可能想要指定 `out` 變數的類型，如上所示。 不過，語言有支援使用隱含型別區域變數︰

[!code-csharp[OutVarVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#02_OutVarVariableDeclarations "Implicitly typed Out variable")]

* 程式碼更容易閱讀與理解。 
    - 您在使用之處宣告 out 變數，而不是在上方另一行。
* 不需要指派初始值。
    - 藉由在方法呼叫中使用之處宣告 `out` 變數，就無法在指派它之前意外使用它。

這項功能最常見的用途是 `Try` 模式。 在此模式中，方法會傳回 `bool`，指出成功或失敗，以及一個 `out` 變數，提供方法成功時的結果。

當使用 `out` 變數宣告時，宣告的變數會「遺漏」到 if 陳述式的外部範圍。 這可讓您在之後使用變數︰

```csharp
if (!int.TryParse(input, out int result))
{    
    return null;
}

return result;
```

## <a name="tuples"></a>Tuple

> [!NOTE]
> 新的 Tuple 功能需要 <xref:System.ValueTuple> 類型。
> 您必須新增 NuGet 套件 [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/)，以將它用於不包含類型的平台。
>
> 這類似於依賴架構中所傳遞類型的其他語言功能。 範例包含依賴 `INotifyCompletion` 介面的 `async` 和 `await`，以及依賴 `IEnumerable<T>` 的 LINQ。 不過，傳遞機制會變更，因為 .NET 變得與平台更為無關。 .NET Framework 可能不會永遠隨附於相同的步調，作為語言編譯器。 如果新語言功能依賴新類型，則在提供語言功能時，會以 NuGet 套件形式提供這些類型。 因為這些新類型會新增至 .NET Standard API 並傳遞為架構的一部分，所以將會移除 NuGet 套件需求。

C# 為類別和結構提供豐富的語法，可用來解釋您的設計目的。 但有時候豐富的語法需要額外的工作才能得到最少的好處。 您可能經常撰寫需要包含多個資料項目之簡單結構的方法。 為了支援這些案例，C# 已新增 *Tuple*。 Tuple 是輕量的資料結構，其中包含多個欄位來代表資料成員。
不會驗證這些欄位，且您不能定義自己的方法

> [!NOTE]
> Tuple 在 C# 7 之前即可使用，但效率不彰且沒有語言支援。
> 這表示 Tuple 元素只能參考為 `Item1` 及 `Item2` 等等。 C# 7 加入了 Tuple 的語言支援，讓 Tuple 欄位的語意名稱能使用全新且更具效率的 Tuple 型別。

您可以指派每個成員到一個值，以建立 Tuple︰

[!code-csharp[UnnamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#04_UnnamedTuple "Unnamed tuple")]

指派會建立成員為 `Item1` 與 `Item2` 的 Tuple，而您能使用與 <xref:System.Tuple> 相同的方式加以使用。您可以變更語法，以建立能夠為 Tuple 中每位成員提供語意名稱的 Tuple：

[!code-csharp[NamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#05_NamedTuple "Named tuple")]

`namedLetters` Tuple 包含稱為 `Alpha` 和 `Beta` 的欄位。 這些名稱只會在編譯時間出現而不會保留，例如在執行階段使用反映調查 Tuple 時。

在 Tuple 指派中，您也可以在指派的右邊，指定欄位的名稱︰

[!code-csharp[ImplicitNamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#06_ImplicitNamedTuple "Implicitly named tuple")]

您可以在指定指派左側及右側的欄位名稱︰

[!code-csharp[NamedTupleConflict](../../../samples/snippets/csharp/new-in-7/program.cs#07_NamedTupleConflict "Named tuple conflict")]

上述列會產生警告 `CS8123`，告訴您指派右邊的名稱 `Alpha` 和 `Beta` 會被忽略，因為它們與左邊的名稱 `First` 和 `Second` 發生衝突。

上述範例顯示宣告 Tuple 的基本語法。 Tuple 最適合用作 `private` 和 `internal` 方法的傳回型別。 Tuple 提供簡單的語法，可讓方法傳回多個離散值︰您節省了撰寫定義傳回型別之 `class` 或 `struct` 的工作。 不需要建立新的類型。

建立 Tuple 更有效率且更具生產力。
它是一個更簡單的輕量語法，可定義攜帶多個值的資料結構。 下列範例方法會傳回在一個整數序列中找到的最小和最大值︰

[!code-csharp[TupleReturningMethod](../../../samples/snippets/csharp/new-in-7/program.cs#08_TupleReturningMethod "Tuple returning method")]

如此來使用 Tuple 可提供數個優點︰

* 您節省了撰寫定義傳回型別之 `class` 或 `struct` 的工作。 
* 您不需要建立新的類型。
* 語言的增強功能可讓您免於呼叫 <xref:System.Tuple.Create``1(``0)> 方法。

方法的宣告提供所傳回 Tuple 欄位的名稱。 當您呼叫的方法時，傳回值是一個 Tuple，其欄位為 `Max` 和 `Min`：

[!code-csharp[CallingTupleMethod](../../../samples/snippets/csharp/new-in-7/program.cs#09_CallingTupleMethod "Calling a tuple returning method")]

有時候您可能會想要解除封裝已從方法傳回的 Tuple 成員。  您可以藉由為 Tuple 中的每個值宣告不同變數來這麼做。 這稱為「解構」Tuple：

[!code-csharp[CallingWithDeconstructor](../../../samples/snippets/csharp/new-in-7/program.cs#10_CallingWithDeconstructor "Deconstructing a tuple")]

<!-- Add wildcards here, if they are in C# 7
-->

您也可以在 .NET 中為任何類型提供類似的解構。 這是藉由撰寫 `Deconstruct` 方法作為類別的成員而達成。 `Deconstruct` 方法為您想要擷取的每個屬性提供一組 `out` 引數。 請考慮這個 `Point` 類別，它會提供 deconstructor 方法，擷取 `X` 和 `Y` 座標︰

[!code-csharp[PointWithDeconstruction](../../../samples/snippets/csharp/new-in-7/point.cs#11_PointWithDeconstruction "Point with deconstruction method")]
 
您可以藉由指派 Tuple 至 `Point` 來擷取個別的欄位：

[!code-csharp[DeconstructPoint](../../../samples/snippets/csharp/new-in-7/program.cs#12_DeconstructPoint "Deconstruct a point")]

您不受限於 `Deconstruct` 方法中定義的名稱。 您可以在指派過程中將擷取變數重新命名︰  

[!code-csharp[DeconstructNames](../../../samples/snippets/csharp/new-in-7/program.cs#13_DeconstructNames "Deconstruct with new names")]

您可以在 [Tuple 主題](../tuples.md)中深入了解 Tuple。

## <a name="discards"></a>Discard 變數

通常在您解構 Tuple 或以 `out` 參數呼叫方法時，會強制您要定義變數，而您無須在意變數的值也沒有使用該值的打算。 C# 新增了對*捨棄*的支援，來應付這種狀況。 Discard 是僅限寫入的變數，其名稱為 `_` (底線字元)；您可將所有想要捨棄的值指派到單一變數。 Discard 變數類似於未經指派的變數；和指派陳述式一樣，都不能用於程式碼中。

下列情況中支援 Discard 變數：

* 解構 Tuple 或使用者定義型別時。

* 以 [out](../language-reference/keywords/out-parameter-modifier.md) 參數呼叫方法時。

* 執行 [is](../language-reference/keywords/is.md) 及 [switch](../language-reference/keywords/switch.md) 陳述式的模式比對作業時。

* 當您想要將指派的值明確識別為 Discard 變數時，可作為獨立識別項使用。

下列範例定義的 `QueryCityDataForYears` 方法，會傳回包含兩個不同年份的城市資料之 6-Tuple。 範例中的方法呼叫只有對方法傳回的兩個母體有效，所以會在解構 Tuple 時，將 Tuple 中剩餘的值視作 Discard 變數來處理。

[!code-csharp[Tuple-discard](../../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

如需詳細資訊，請參閱 [Discard](../discards.md)。
 
## <a name="pattern-matching"></a>模式比對

「模式比對」是一項功能，可讓您對物件類型以外的屬性實作方法分派。 您可能已經熟悉根據物件類型的方法分派。 在物件導向程式設計中，虛擬和覆寫方法可提供語言語法，以實作根據物件類型的方法分派。 基底和衍生類別能提供不同的實作。 模式比對運算式會擴充這個概念，讓您可以輕鬆地為不是透過繼承階層架構而關聯的類型和資料項目實作類似的分派模式。 

模式比對支援 `is` 運算式和 `switch` 運算式。 每個都讓您能檢查物件和其屬性，以判斷該物件是否符合搜尋的模式。 您使用 `when` 關鍵字來指定其他規則給該模式。

### <a name="is-expression"></a>`is` 運算式

`is` 模式運算式會擴充熟悉的 `is` 運算子，來查詢其類型之外的物件。

舉個簡單的案例。 我們會將功能加入此案例中，示範模式比對運算式如何讓處理非相關類型的演算法變簡單。 我們將從計算數次擲骰子總和的方法開始︰

[!code-csharp[SumDieRolls](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#14_SumDieRolls "Sum die rolls")]

您可能會很快發現您需要找出部分擲骰情況是以多個骰子所擲出的擲骰子總和。 輸入序列的一部分可能是多個結果，而不是單一數字︰

[!code-csharp[SumDieRollsWithGroups](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#15_SumDieRollsWithGroups "Sum die rolls with groups")]

`is` 模式運算式非常適合此案例。 在檢查類型時，您可以撰寫變數的初始化。 這會為已驗證的執行階段型別建立新的變數。

當您繼續擴充這些案例時，您可能會發現您建立了更多 `if` 和 `else if` 陳述式。 變得不便之後，您可能會想要切換至 `switch` 模式運算式。

### <a name="switch-statement-updates"></a>`switch` 陳述式更新

「比對運算式」的語法很熟悉，是根據已屬於 C# 語言一部分的 `switch` 陳述式。 讓我們先轉譯現有程式碼，使用比對運算式，之後才新增案例︰ 

[!code-csharp[SumUsingSwitch](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#16_SumUsingSwitch "Sum using switch")]

比對運算式的語法與 `is` 運算式稍微不同，您可在 `case` 運算式的開頭宣告類型和變數。

比對運算式也支援常數。 如此可以節省時間，因為已隔離簡單的案例︰

[!code-csharp[SwitchWithConstants](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#17_SwitchWithConstants "Switch with constants")]

上述程式碼會新增 `0` 的案例作為 `int` 的特殊案例，並新增 `null` 作為沒有輸入時的特殊案例。 這示範了參數模式運算式中的一個重要新功能︰`case` 運算式的順序現在有其重要性。 `0` 案例必須出現在一般 `int` 案例之前。 否則，第一個符合的模式將是 `int` 案例，即使值是 `0`。 如果您意外排列比對運算式，以致排列較後的案例已經過處理，則編譯器會將其加上旗標並產生錯誤。

這個相同的行為可啟用空輸入序列的特殊案例。
您可以看到，具有項目之 `IEnumerable` 項目的案例，必須出現在一般 `IEnumerable` 案例之前。

此版本也新增了 `default` 案例。 `default` 案例一律會最後評估，不論它出現在來源中的順序為何。 因此，慣例是將 `default` 案例放到最後。

最後，我們要新增最後一個新骰子樣式的 `case`。 某些遊戲使用百分位數骰子來代表更大範圍的數字。 

> [!NOTE]
> 兩個 10 面的百分位數骰子可以代表從 0 到 99 的每個數字。 一顆骰子的邊已標示為 `00`、`10`、`20`...`90`。 另一顆骰子的邊已標示為 `0`、`1`、`2`...`9`。 將兩個骰子值相加，您就可以得到 0 到 99 的每個數字。

若要將這種骰子新增至集合，請先定義代表百分位數骰子的類型。 `TensDigit` 屬性可儲存值 `0`、`10`、`20`，最高到 `90`：

[!code-csharp[18_PercentileDice](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#18_PercentileDice "Percentile Die type")]

然後，新增新類型的 `case` 比對運算式︰

[!code-csharp[SwitchWithNewTypes](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#19_SwitchWithNewTypes "Include Percentile Die type")]

模式比對運算式的新語法可讓您更輕鬆地根據物件的類型或其他屬性建立分派演算法，並使用清楚且簡潔的語法。 模式比對運算式可讓在繼承方面不相關的資料類型上啟用這些建構。

您可以在 [C# 中的模式比對](../pattern-matching.md)專門主題中深入了解模式比對。

## <a name="ref-locals-and-returns"></a>Ref 區域變數和傳回

這項功能可以啟用使用和傳回在其他地方定義之變數參考的演算法。 其中一個範例是使用大型矩陣，並尋找具有特定特性的單一位置。 一種方法會傳回矩陣中單一位置的兩個索引︰

[!code-csharp[FindReturningIndices](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#20_FindReturningIndices "Find returning indices")]

這個程式碼有許多問題。 首先，它是傳回 Tuple 的公用方法。 語言支援此做法，但公用 API 是慣用的使用者定義型別 (類別或結構)。

第二，這個方法會傳回矩陣中之項目的索引。
那會導致呼叫端撰寫程式碼，使用那些索引來對矩陣進行取值，並修改單一項目︰

[!code-csharp[UpdateItemFromIndices](../../../samples/snippets/csharp/new-in-7/program.cs#21_UpdateItemFromIndices "Update Item From Indices")]

相反地，您可以撰寫方法，傳回對您想要變更之矩陣項目的「參考」。 在舊版本中，您只能使用不安全的程式碼，並傳回對 `int` 的指標來完成這項作業。

讓我們逐步解說一系列的變更，以展示 ref 區域功能，並示範如何建立傳回對內部儲存體之參考的方法。
在過程中，您將了解 ref 傳回和 ref 區域功能的規則，避免您不小心誤用。

一開始先修改 `Find` 方法宣告，讓它傳回 `ref int` 而不是 Tuple。 然後，修改 return 陳述式，讓它傳回儲存在矩陣中的值，而不是兩個索引︰

```csharp
// Note that this won't compile. 
// Method declaration indicates ref return,
// but return statement specifies a value return.
public static ref int Find2(int[,] matrix, Func<int, bool> predicate)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
        for (int j = 0; j < matrix.GetLength(1); j++)
            if (predicate(matrix[i, j]))
                return matrix[i, j];
    throw new InvalidOperationException("Not found");
}
```

當您宣告方法會傳回 `ref` 變數時，您也必須將 `ref` 關鍵字加入每個 return 陳述式。 那表示是以傳址方式傳回，並可協助稍後閱讀程式碼的開發人員記得該方法會以傳址方式傳回︰

[!code-csharp[FindReturningRef](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#22_FindReturningRef "Find returning by reference")]

既然方法會傳回矩陣中整數值的參考，您需要修改呼叫它的位置。  `var` 宣告表示 `valItem` 現在是 `int`，而不是 Tuple：

[!code-csharp[AssignRefReturnToValue](../../../samples/snippets/csharp/new-in-7/program.cs#23_AssignRefReturnToValue "Assign ref return to value")]

在上述範例中的第二個 `WriteLine` 陳述式會列印出值 `42`，而非 `24`。 變數 `valItem` 是 `int`，而非 `ref int`。 `var` 關鍵字可讓編譯器指定類型，但不會隱含地新增 `ref` 修飾詞。 相反地，`ref return` 所指的值會「複製」到指派左手邊的變數。 變數不是 `ref` 區域變數。

若要取得您想要的結果，您需要將 `ref` 修飾詞加入區域變數宣告，當傳回值是參考時，讓變數成為參考︰

[!code-csharp[AssignRefReturn](../../../samples/snippets/csharp/new-in-7/program.cs#24_AssignRefReturn "Assign ref return")]

現在，在上述範例中的第二個 `WriteLine` 陳述式會印出值 `24`，表示已修改矩陣中的儲存體。 區域變數已使用 `ref` 修飾詞宣告，而且它需要 `ref` 傳回。 您必須在宣告 `ref` 變數時先初始化，您無法分割宣告和初始化。

C# 語言有三個其他的規則可保護您免於濫用 `ref` 區域變數和傳回值︰

* 您無法將標準方法傳回值指派到 `ref` 區域變數。
    - 這可杜絕類似 `ref int i = sequence.Count();` 的陳述式
* 您不能傳回 `ref` 給變數，而該變數存留期不超過方法的執行。
    - 這表示您無法將參考傳回區域變數或類似範圍的變數。
* `ref` 區域變數及傳回值無法配合非同步方法使用。
    - 當非同步方法傳回時，編譯器無法確定參考的變數是否已設定為其最終的值。

新增 ref 區域變數和 ref 傳回能啟用更有效率的演算法，因為可以避免複製值，或是多次執行取值作業。 

## <a name="local-functions"></a>區域函式

類別的許多設計都包括從唯一一個位置呼叫的方法。 這些額外的私用方法會使每一種方法維持小而聚焦。 然而，它們可能使得在第一次閱讀時更難了解類別。 您必須在單一呼叫位置的內容之外了解這些方法。

對於這些設計，「區域函式」可讓您在另個方法的內容中宣告方法。 這使得類別的讀者比較容易看到區域方法只會從它宣告之處的內容呼叫。

有兩個很常見的區域函式使用案例︰公用 Iterator 方法和公用非同步方法。 這兩種方法都會產生程式碼，比程式設計人員想像更晚才報告錯誤。 在 Iterator 方法的情況下，任何例外狀況只會在呼叫列舉傳回序列的程式碼時觀察到。 若是非同步方法，任何例外狀況只會在傳回的 `Task` 等候時觀察到。

讓我們從 Iterator 方法開始︰

[!code-csharp[IteratorMethod](../../../samples/snippets/csharp/new-in-7/Iterator.cs#25_IteratorMethod "Iterator method")]

檢查不正確地呼叫 Iterator 方法的下列程式碼︰

[!code-csharp[CallIteratorMethod](../../../samples/snippets/csharp/new-in-7/program.cs#26_CallIteratorMethod "Call iterator method")]

`resultSet` 反覆執行時會擲回例外狀況，而不是在建立 `resultSet` 時。
在這個包含的範例中，大部分開發人員可以快速地診斷問題。 不過，在較大的程式碼基底中，建立迭代器的程式碼經常不那麼接近列舉結果的程式碼。 您可以重構程式碼，使公用方法驗證所有引數，而私用方法則產生列舉︰

[!code-csharp[IteratorMethodRefactored](../../../samples/snippets/csharp/new-in-7/Iterator.cs#27_IteratorMethodRefactored "Iterator method refactored")]

這個重構的版本會立即擲回例外狀況，因為公用方法不是 Iterator 方法。只有私用方法會使用 `yield return` 語法。 不過，這項重構功能有潛在問題。 私用方法應該只從公用介面方法呼叫，因為否則會略過所有引數的驗證。
類別的讀者必須閱讀整個類別，並尋找對 `alphabetSubsetImplementation` 方法的任何其他參考，以探索這項事實。

您可以藉由宣告 `alphabetSubsetImplementation` 為公用 API 方法內的區域函式，讓該項設計目的更清楚︰

[!code-csharp[22_IteratorMethodLocal](../../../samples/snippets/csharp/new-in-7/Iterator.cs#28_IteratorMethodLocal "Iterator method with local function")]

上述的版本已闡明區域方法只會在外部方法的內容中參考。 區域函式的規則也確保開發人員無法意外從類別中的另一個位置呼叫區域函式，並略過引數的驗證。

相同的技巧也可以運用在 `async` 方法，以確保在非同步工作開始之前，會擲回引數驗證所引發的例外狀況︰

[!code-csharp[TaskExample](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

> [!NOTE]
> 區域函式支援的部分設計也可以使用「Lambda 運算式」完成。 有興趣的人可以[進一步了解差異](../local-functions-vs-lambdas.md)

## <a name="more-expression-bodied-members"></a>更多運算式主體成員

C# 6 引進了成員函式的[運算式主體成員](csharp-6.md#expression-bodied-function-members)和唯讀屬性。 C# 7 展開了可以實作為運算式的允許成員。 在 C# 7 中，您可以實作「建構函式」、「完成項」，以及「屬性」和「索引子」上的 `get` 和 `set` 存取子。 下列程式碼將示範各項的範例：

[!code-csharp[ExpressionBodiedMembers](../../../samples/snippets/csharp/new-in-7/expressionmembers.cs#36_ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> 這個範例不需要完成項，但仍加以顯示以示範語法。 除非為釋放 Unmanaged 資源所需，否則不應該在類別中實作完成項。 您也應該考慮使用 <xref:System.Runtime.InteropServices.SafeHandle> 類別而不是直接管理 Unmanaged 資源。

這些運算式主體成員的新位置代表 C# 語言的重要里程碑︰這些功能是由參與開放原始碼 [Roslyn](https://github.com/dotnet/Roslyn) 專案的社群成員所實作。

## <a name="throw-expressions"></a>throw 運算式

在 C# 中，`throw` 一直都是陳述式。 因為 `throw` 是陳述式，而不是運算式，所以有您無法在其中使用它的 C# 建構。 這些包含條件運算式、Null 聯合運算式和一些 Lambda 運算式。 新增運算式主體成員會新增 `throw` 運算式適用的更多位置。 為了讓您可以撰寫任何這些建構，C# 7 引進了「Throw 運算式」。

語法與您一直用於 `throw` 陳述式的語法相同。 唯一的差別在於現在您可以將它們放在新位置，例如在條件運算式中︰

[!code-csharp[Throw_ExpressionExample](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#37_Throw_ExpressionExample "conditional throw expressions")]

此功能可讓您在初始化運算式中使用 throw 運算式︰

[!code-csharp[ThrowInInitialization](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#38_ThrowInInitialization "conditional throw expressions")]

過去，這些初始設定需要在建構函式中，且 throw 陳述式在建構函式主體中︰


[!code-csharp[ThrowInConstructor](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#39_ThrowInConstructor "throw statements")]

> [!NOTE]
> 上述兩個建構會造成在物件建構期間擲回例外狀況。 這些通常很難復原。
> 因此，不建議使用會在建構期間擲回例外狀況的設計。

## <a name="generalized-async-return-types"></a>通用的非同步傳回型別

從非同步方法傳回 `Task` 物件可能會造成在特定路徑的效能瓶頸。 `Task` 是參考型別，因此使用它表示要配置物件。 當使用 `async` 修飾詞宣告的方法傳回快取的結果時，或是以同步方式完成，額外配置可能會在效能關鍵的程式碼區段中變成一項重要的時間成本。 如果這些配置發生在緊密迴圈中的話，它可能會變得成本很高。

新語言功能表示非同步方法除了 `Task`、`Task<T>` 和 `void` 之外，可能還會傳回其他型別。 傳回的型別仍然必須滿足非同步模式，也就是表示 `GetAwaiter` 方法必須可存取。 具體的範例就是，`ValueTask` 類型已新增到 .NET Framework，才便利用這項新的語言功能︰ 

[!code-csharp[UsingValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#30_UsingValueTask "Using ValueTask")]

> [!NOTE]
> 您必須新增 NuGet 套件 [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/)，才可使用 <xref:System.Threading.Tasks.ValueTask%601> 類型。

簡單的最佳化就是使用 `ValueTask` 取代過去使用 `Task` 之處。 不過，如果您想要以手動方式執行額外的最佳化，可以快取來自非同步工作的結果，並在後續的呼叫中重複使用結果。 `ValueTask` 結構有一個具有 `Task` 參數的建構函式，讓您可以從任何現有非同步方法的傳回值來建構 `ValueTask`︰

[!code-csharp[AsyncOptimizedValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#31_AsyncOptimizedValueTask "Return async result or cached value")]
 
如同所有的效能建議，您應該先評定這兩個版本，再進行大規模的程式碼變更。

## <a name="numeric-literal-syntax-improvements"></a>數值常值的語法增強功能

錯譯數值常數，可能會使得在第一次閱讀它時，更加難以了解程式碼。 這通常發生於那些數字用作位元遮罩或其他符號而不是數字值的時候。 C# 7 包含兩項新功能，可以更輕鬆地以預期用途最容易閱讀的方式來撰寫數字︰「二進位常值」和「數字分隔符號」。

當您在建立位元遮罩時，或是每當數字的二進位表示法構成最容易閱讀的程式碼時，請以二進位撰寫該數字︰

[!code-csharp[BinaryConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#32_BinaryConstants "Binary constants")]

常數開頭的 `0b` 表示數字是撰寫為二進位數字。

二進位數字可能會很長，因此引進 `_` 作為千位分隔符號通常能夠更輕鬆地查看位元模式︰

[!code-csharp[ThousandSeparators](../../../samples/snippets/csharp/new-in-7/Program.cs#33_ThousandSeparators "Thousands separators")]

千位分隔符號可以出現在常數的任何位置。 對於以 10 為底的數字，通常會使用它作為千位分隔符號︰

[!code-csharp[LargeIntegers](../../../samples/snippets/csharp/new-in-7/Program.cs#34_LargeIntegers "Large integer")]

千位分隔符號也可以搭配 `decimal`、`float` 和 `double` 類型︰

[!code-csharp[OtherConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#35_OtherConstants "non-integral constants")]

結合起來，您在宣告數值常數時可以有更多的可讀性。

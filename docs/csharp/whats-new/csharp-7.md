---
title: C# 7.0 的新功能 - C# 指南
description: 取得 C# 語言版本 7.0 中新功能的概觀。
ms.date: 02/20/2019
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 0f26a9647503ebb667d961fefaa05a25a71ec6f5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926566"
---
# <a name="whats-new-in-c-70"></a>C# 7.0 的新功能

C# 7.0 新增許多新功能至 C# 語言：

- [`out` 變數](#out-variables)
  - 您可以宣告 `out` 內嵌值作為使用它們之方法的引數。
- [元組](#tuples)
  - 您可以建立包含多個公用欄位的輕量、未具名的類型。 編譯器和 IDE 工具了解這些類型的語意。
- [捨棄](#discards)
  - 捨棄是當您不在意指派的值時，於指派內使用的僅限寫入且暫時之變數。 解構 Tuple 及使用者定義型別，以及使用 `out` 參數呼叫方法時，捨棄最為實用。
- [模式比對](#pattern-matching)
  - 您可以建立以任意類型和這些類型成員的值為基礎的分支邏輯。
- [`ref` 區域變數和傳回](#ref-locals-and-returns)
  - 方法區域變數和傳回值可以是其他儲存體的參考。
- [區域函式](#local-functions)
  - 您可以將函式巢狀放置在其他函式內，限制其範圍和可視性。
- [更多運算式主體成員](#more-expression-bodied-members)
  - 可以使用運算式來撰寫的成員清單已經增長。
- [`throw`運算式](#throw-expressions)
  - 您可以在程式碼建構中擲回例外狀況 (因為先前 `throw` 是陳述式，所以您無法這麼做)。
- [通用的非同步傳回型別](#generalized-async-return-types)
  - 使用 `async` 修飾詞宣告的方法除了 `Task` 和 `Task<T>` 之外，也能傳回其他類型。
- [數值常值語法增強功能](#numeric-literal-syntax-improvements)
  - 新的語彙基元改善了數值常數的可讀性。

此文章的其餘部分將概述各個功能。 您將了解每項功能背後的原因。 您將了解語法。 您可以使用 `dotnet try` 全域工具，在您的環境中探索這些功能：

1. 安裝 [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) 全域工具。
1. 複製 [dotnet/try-samples](https://github.com/dotnet/try-samples) 存放庫。
1. 將目前目錄設為 *try-samples* 存放庫的 *csharp7* 子目錄。
1. 執行 `dotnet try`。

## <a name="out-variables"></a>`out` 變數

在這個版本中，支援 `out` 參數的現有語法已經過改善。 您現在可以在方法呼叫的引數清單中宣告 `out` 變數，而不是撰寫個別的宣告陳述式︰

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

為了清楚起見，您可能想要指定 `out` 變數的類型，如上所示。 不過，語言有支援使用隱含型別區域變數︰

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- 程式碼更容易閱讀與理解。
  - 您在使用之處宣告 out 變數，而不是在上方另一行。
- 不需要指派初始值。
  - 藉由在方法呼叫中使用所在宣告 `out` 變數，就不會在指派它之前意外使用它。

## <a name="tuples"></a>Tuple

C# 為類別和結構提供豐富的語法，可用來解釋您的設計目的。 但有時候豐富的語法需要額外的工作才能得到最少的好處。 您可能經常撰寫需要包含多個資料項目之簡單結構的方法。 為了支援這些案例，C# 已新增 *Tuple*。 Tuple 是輕量的資料結構，其中包含多個欄位來代表資料成員。
這些欄位不會經過驗證，且您無法定義自己的方法

> [!NOTE]
> Tuple 在 C# 7.0 之前即可使用，但效率不彰且沒有語言支援。
> 這表示元組元素只能參考為 `Item1`及 `Item2` 等等。 C# 7.0 加入了 Tuple 的語言支援，讓 Tuple 欄位的語意名稱能使用全新且更具效率的 Tuple 型別。

您可以將值指派給每個成員，並選擇性地提供語意名稱給每個 Tuple 的成員，以建立 Tuple：

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

`namedLetters` Tuple 包含稱為 `Alpha` 和 `Beta` 的欄位。 這些名稱只會在編譯時間存在而不會保留 (例如，在執行階段使用反映調查 Tuple 時)。

在 Tuple 指派中，您也可以在指派的右邊，指定欄位的名稱︰

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

有時候您可能會想要解除封裝已從方法傳回的 Tuple 成員。  您可以藉由為 Tuple 中的每個值宣告不同變數來這麼做。 這種解除封裝稱為*解構* Tuple：

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

您也可以在 .NET 中為任何類型提供類似的解構。 您可以將 `Deconstruct` 方法撰寫為類別的成員。 `Deconstruct` 方法為您想要擷取的每個屬性提供一組 `out` 引數。 請考慮這個 `Point` 類別，它會提供 deconstructor 方法，擷取 `X` 和 `Y` 座標︰

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

您可以藉由將 `Point` 指派給 Tuple 來擷取個別的欄位：

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

您可以在 [Tuple 文章](../tuples.md)中深入了解 Tuple。

## <a name="discards"></a>捨棄

通常在您解構元組或以 `out` 參數呼叫方法時，會強制您要定義變數，而您無須在意變數的值也沒有使用該值的打算。 C# 新增了對*捨棄*的支援，來應付這種狀況。 捨棄是僅限寫入的變數，其名稱為 `_` (底線字元)；您可將所有想要捨棄的值指派到單一變數。 捨棄類似於未經指派的變數；和指派陳述式一樣，都不能用於程式碼中。

下列情況中支援捨棄：

- 解構元組或使用者定義型別時。
- 以 [out](../language-reference/keywords/out-parameter-modifier.md) 參數呼叫方法時。
- 執行 [is](../language-reference/keywords/is.md) 及 [switch](../language-reference/keywords/switch.md) 陳述式的模式比對作業時。
- 作為獨立識別項，當您想要將指派的值明確識別為捨棄時。

下列範例定義的 `QueryCityDataForYears` 方法，會傳回包含兩個不同年份之城市資料的 6 元組。 範例中的方法呼叫只有對方法傳回的兩個母體有效，所以會在解構元組時，將元組中剩餘的值視作捨棄處理。

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

如需詳細資訊，請參閱[捨棄](../discards.md)。

## <a name="pattern-matching"></a>模式比對

「模式比對」是一項功能，可讓您對物件類型以外的屬性實作方法分派。 您可能已經熟悉根據物件類型的方法分派。 在物件導向程式設計中，虛擬和覆寫方法可提供語言語法，以根據物件的類型實作方法分派。 基底和衍生類別能提供不同的實作。
模式比對運算式會擴充這個概念，讓您可以輕鬆地為不是透過繼承階層架構而關聯的類型和資料元素實作類似的分派模式。

模式比對支援 `is` 運算式和 `switch` 運算式。 每個都讓您能檢查物件和其屬性，以判斷該物件是否符合搜尋的模式。 您使用 `when` 關鍵字來指定其他規則給該模式。

`is` 模式運算式會擴充熟悉的 [`is` 運算子](../language-reference/keywords/is.md#pattern-matching-with-is)，來查詢其類型的相關物件，並使用一個指令指派結果。 下列程式碼會檢查變數是否為 `int`，如果是，則將其加入至目前的總和：

```csharp
if (input is int count)
    sum += count;
```

上述的小範例示範 `is` 運算式的增強功能。 您可以對實值型別以及參考型別進行測試，而且您可以將成功的結果指派給正確型別的新變數。

switch 比對運算式的語法很熟悉，是以已屬於 C# 語言一部分的 `switch` 陳述式為基礎。 更新的 switch 陳述式有數個新的建構：

- `switch` 運算式的控管型別不再限於整數型別、`Enum` 型別、`string`，或對應至這些其中一種類型的可為 Null 的型別。 可以使用任何型別。
- 您可以測試每個 `case` 標籤中的 `switch` 運算式型別。 如同使用 `is` 運算式，您可以將新的變數指派給該型別。
- 您可以加入 `when` 子句，以進一步測試該變數的條件。
- `case` 標籤的順序現在很重要。 系統會執行要比對的第一個分支；其他則會略過。

下列程式碼可示範這些新功能：

```csharp
public static int SumPositiveNumbers(IEnumerable<object> sequence)
{
    int sum = 0;
    foreach (var i in sequence)
    {
        switch (i)
        {
            case 0:
                break;
            case IEnumerable<int> childSequence:
            {
                foreach(var item in childSequence)
                    sum += (item > 0) ? item : 0;
                break;
            }
            case int n when n > 0:
                sum += n;
                break;
            case null:
                throw new NullReferenceException("Null found in sequence");
            default:
                throw new InvalidOperationException("Unrecognized type");
        }
    }
    return sum;
}
```

- `case 0:` 是熟悉的常數模式。
- `case IEnumerable<int> childSequence:` 是一種型別模式。
- `case int n when n > 0:` 是一種具有其他 `when` 條件的型別模式。
- `case null:` 是 Null 模式。
- `default:` 是熟悉的預設案例。

您可以在 [C# 中的模式比對](../pattern-matching.md)中深入了解模式比對。

## <a name="ref-locals-and-returns"></a>Ref 區域變數和傳回

這項功能可以啟用使用和傳回在其他地方定義之變數參考的演算法。 其中一個範例是使用大型矩陣，並尋找具有特定特性的單一位置。 下列方法會傳回矩陣中該儲存體的**參考**：

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

您可以將傳回值宣告為 `ref`，並在矩陣中修改該值，如下列程式碼所示：

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

C# 語言具備數個規則，可防止您濫用 `ref` 區域變數並傳回︰

- 您必須將 `ref` 關鍵字加入至方法特徵標記，以及某個方法中的所有 `return` 陳述式。
  - 如此可透過整個方法的參考，清除方法傳回。
- `ref return` 可能會指派給值變數，或 `ref` 變數。
  - 呼叫端會控制是否要複製傳回值。 指派傳回值時省略 `ref` 修飾詞表示呼叫端需要值的複本，而不是儲存體的參考。
- 您無法將標準方法傳回值指派到 `ref` 區域變數。
  - 這可杜絕類似 `ref int i = sequence.Count();` 的陳述式
- 您無法將 `ref` 傳回給其存留期不超過方法執行的變數。
  - 這表示您無法將參考傳回區域變數或具有類似範圍的變數。
- `ref` 區域變數及傳回值無法配合非同步方法使用。
  - 當非同步方法傳回時，編譯器無法確定參考的變數是否已設定為其最終的值。

新增 ref 區域變數和 ref 傳回能啟用更有效率的演算法，因為可以避免複製值，或是多次執行取值作業。

將 `ref` 新增至傳回值是[來源相容變更](version-update-considerations.md#source-compatible-changes)。 現有程式碼會編譯，但是 ref 傳回值是在指派時複製。 呼叫端必須將傳回值的儲存體更新為 `ref` 區域變數，將傳回項目儲存為參考。

如需詳細資訊，請參閱 [ref 關鍵字](../language-reference/keywords/ref.md)一文。

## <a name="local-functions"></a>區域函式

類別的許多設計都包括從唯一一個位置呼叫的方法。 這些額外的私用方法會使每一種方法維持小而聚焦。 「區域函式」可讓您在另一個方法的內容中宣告方法。 區域函式可讓類別讀者輕鬆查看區域方法只會從其宣告的內容中呼叫。

有兩個常見的區域函式使用案例︰公用迭代器方法和公用非同步方法。 這兩種方法都會產生程式碼，比程式設計人員想像更晚才報告錯誤。 在迭代器方法中，任何例外狀況只會在呼叫列舉傳回序列的程式碼時觀察到。 在非同步方法中，任何例外狀況只會在傳回的 `Task` 等候時觀察到。 下列範例示範使用區域函式分隔參數驗證和迭代器實作：

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

相同的技巧也可以運用在 `async` 方法，以確保在非同步工作開始之前，會擲回引數驗證所引發的例外狀況︰

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

> [!NOTE]
> 區域函式支援的部分設計也可以使用「Lambda 運算式」完成。 有興趣的人可以[進一步了解差異](../local-functions-vs-lambdas.md)

## <a name="more-expression-bodied-members"></a>更多運算式主體成員

C# 6 引進了成員函式的[運算式主體成員](csharp-6.md#expression-bodied-function-members)和唯讀屬性。 C# 7.0 擴充了可以實作為運算式的允許成員。 在 C# 7.0 中，您可以實作「建構函式」、「完成項」，以及「屬性」和「索引子」上的 `get` 和 `set` 存取子。 下列程式碼將示範各項的範例：

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> 這個範例不需要完成項，但仍加以顯示以示範語法。 除非為釋放 Unmanaged 資源所需，否則不應該在類別中實作完成項。 您也應該考慮使用 <xref:System.Runtime.InteropServices.SafeHandle> 類別而不是直接管理 Unmanaged 資源。

這些運算式主體成員的新位置代表 C# 語言的重要里程碑︰這些功能是由參與開放原始碼 [Roslyn](https://github.com/dotnet/Roslyn) 專案的社群成員所實作。

將方法變更為運算式主體成員是[二進位相容](version-update-considerations.md#binary-compatible-changes)變更。

## <a name="throw-expressions"></a>throw 運算式

在 C# 中，`throw` 一直都是陳述式。 因為 `throw` 是陳述式，而不是運算式，所以有您無法在其中使用它的 C# 建構。 這些包含條件運算式、Null 聯合運算式和一些 Lambda 運算式。 新增運算式主體成員會新增 `throw` 運算式適用的更多位置。 為了讓您可以撰寫任何這些建構，C# 7.0 引進了 [*throw 運算式*](../language-reference/keywords/throw.md#the-throw-expression)。

此新增可讓您更輕鬆地撰寫更多以運算式為基礎的程式碼。 您不需要額外的陳述式就可以進行錯誤檢查。

## <a name="generalized-async-return-types"></a>通用的非同步傳回型別

從非同步方法傳回 `Task` 物件可能會造成在特定路徑的效能瓶頸。 `Task` 是參考型別，因此使用它表示要配置物件。 當使用 `async` 修飾詞宣告的方法傳回快取的結果時，或是以同步方式完成，額外配置可能會在效能關鍵的程式碼區段中變成一項重要的時間成本。 如果這些配置發生在緊密迴圈中，它可能會變得成本很高。

新的語言功能表示 async 方法傳回型別不限於 `Task`、`Task<T>` 和 `void`。 傳回的型別仍然必須滿足非同步模式，也就是表示 `GetAwaiter` 方法必須可存取。 具體的範例就是，`ValueTask` 類型已新增到 .NET Framework，才便利用這項新的語言功能︰

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> 您必須新增 NuGet 套件 [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/)，才可使用 <xref:System.Threading.Tasks.ValueTask%601> 類型。

這項增強功能最能幫助程式庫作者避免在效能關鍵的程式碼中配置 `Task`。

## <a name="numeric-literal-syntax-improvements"></a>數值常值的語法增強功能

錯譯數值常數，可能會使得在第一次閱讀它時，更加難以了解程式碼。 位元遮罩或其他符號值容易遭到誤解。 C# 7.0 包含兩項新功能，可以用預期用途最容易閱讀的方式來撰寫數字︰「二進位常值」和「數字分隔符號」。

當您在建立位元遮罩時，或是每當數字的二進位表示法構成最容易閱讀的程式碼時，請以二進位撰寫該數字︰

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

常數開頭的 `0b` 表示數字是撰寫為二進位數字。 二進位數字可能會很長，因此引進 `_` 作為數字分隔符號通常能夠更輕鬆地查看位元模式，如上述的二進位常數所示。 千位分隔符號可以出現在常數的任何位置。 對於以 10 為底的數字，通常會使用它作為千位分隔符號︰

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

千位分隔符號也可以搭配 `decimal`、`float` 和 `double` 類型使用︰

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

結合起來，您在宣告數值常數時可以有更多的可讀性。

---
title: C# 7.0 的新功能 - C# 指南
description: 取得 C# 語言版本 7.0 中新功能的概觀。
ms.date: 10/02/2020
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: c238439b0f435e579d932b3b1eb13e9b0061fa5f
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678231"
---
# <a name="whats-new-in-c-70-through-c-73"></a>C # 7.0 到 c # 7.3 的新功能

C # 7.0 到 c # 7.3 針對您使用 c # 的開發體驗引進了許多功能和累加的改進。 本文概要說明新的語言功能和編譯器選項。 描述說明 c # 7.3 的行為，這是 .NET Framework 架構應用程式所支援的最新版本。

[語言版本選取](../language-reference/configure-language-version.md)設定專案是使用 c # 7.1 新增的，可讓您在專案檔中指定編譯器語言版本。

C # 7.0-7.3 將這些功能和主題新增至 c # 語言：

- [元組和捨棄](#tuples-and-discards)
  - 您可以建立包含多個公用欄位的輕量、未具名的類型。 編譯器和 IDE 工具了解這些類型的語意。
  - 捨棄是當您不在意指派的值時，於指派內使用的僅限寫入且暫時之變數。 解構 Tuple 及使用者定義型別，以及使用 `out` 參數呼叫方法時，捨棄最為實用。
- [模式比對](#pattern-matching)
  - 您可以建立以任意類型和這些類型成員的值為基礎的分支邏輯。
- [`async``Main`方法](#async-main)
  - 應用程式的進入點允許使用`async`修飾詞。
- [區域函數](#local-functions)
  - 您可以將函式巢狀放置在其他函式內，限制其範圍和可視性。
- [更多運算式主體成員](#more-expression-bodied-members)
  - 可以使用運算式來撰寫的成員清單已經增長。
- [`throw` 表達 式](#throw-expressions)
  - 您可以在程式碼建構中擲回例外狀況 (因為先前 `throw` 是陳述式，所以您無法這麼做)。
- [`default` 常值運算式](#default-literal-expressions)
  - 目標類型可以推斷時，可以在預設值運算式中使用預設常值運算式。
- [數值常值的語法增強功能](#numeric-literal-syntax-improvements)
  - 新的語彙基元改善了數值常數的可讀性。
- [`out` 變數](#out-variables)
  - 您可以宣告 `out` 內嵌值作為使用它們之方法的引數。
- [非後置具名引數](#non-trailing-named-arguments)
  - 具名引數之後可以接著位置引數。
- [`private protected` 存取修飾詞](#private-protected-access-modifier)
  - 您可利用 `private protected` 存取修飾詞，存取相同組件中的衍生類別。
- [改進的多載解析](#improved-overload-candidates)
  - 解決多載解析不明確的新規則。
- [撰寫安全、有效率之程式碼的技巧](#enabling-more-efficient-safe-code)
  - 此為語法改進功能組合，其可讓使用參考語意進行實質型別作業變得可能。

最後，編譯器有新的選項：

- `-refout` 以及 `-refonly` 該控制項 [參考元件的產生](#reference-assembly-generation)。
- `-publicsign`，用來啟用組件的開放原始碼軟體 (OSS) 簽署。
- `-pathmap`，用來提供來源目錄的對應。

此文章的其餘部分將概述各個功能。 針對每項功能，您將瞭解其背後的原因和語法。 您可以使用 `dotnet try` 全域工具，在您的環境中探索這些功能：

1. 安裝 [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) 全域工具。
1. 複製 [dotnet/try-samples](https://github.com/dotnet/try-samples) 存放庫。
1. 將目前目錄設為 *try-samples* 存放庫的 *csharp7* 子目錄。
1. 執行 `dotnet try`。

## <a name="tuples-and-discards"></a>元組和捨棄

C# 為類別和結構提供豐富的語法，可用來解釋您的設計目的。 但有時候豐富的語法需要額外的工作才能得到最少的好處。 您可能經常撰寫需要包含多個資料項目之簡單結構的方法。 為了支援這些案例，C# 已新增 *Tuple*。 Tuple 是輕量的資料結構，其中包含多個欄位來代表資料成員。 這些欄位不會經過驗證，且您無法定義自己的方法。 C # 元組類型支援 `==` 和 `!=` 。 如需詳細資訊，

> [!NOTE]
> Tuple 在 C# 7.0 之前即可使用，但效率不彰且沒有語言支援。 這表示元組元素只能參考為 `Item1`及 `Item2` 等等。 C# 7.0 加入了 Tuple 的語言支援，讓 Tuple 欄位的語意名稱能使用全新且更具效率的 Tuple 型別。

您可以將值指派給每個成員，並選擇性地提供語意名稱給每個 Tuple 的成員，以建立 Tuple：

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

`namedLetters` Tuple 包含稱為 `Alpha` 和 `Beta` 的欄位。 這些名稱只會在編譯時期存在，而且不會保留，例如在執行時間使用反映檢查元組時。

在 Tuple 指派中，您也可以在指派的右邊，指定欄位的名稱︰

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

有時候您可能會想要解除封裝已從方法傳回的 Tuple 成員。  您可以藉由為 Tuple 中的每個值宣告不同變數來這麼做。 這種解除封裝稱為 *解構* Tuple：

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

您也可以在 .NET 中為任何類型提供類似的解構。 您可以將 `Deconstruct` 方法撰寫為類別的成員。 `Deconstruct` 方法為您想要擷取的每個屬性提供一組 `out` 引數。 請考慮這個 `Point` 類別，它會提供 deconstructor 方法，擷取 `X` 和 `Y` 座標︰

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

您可以藉由將 `Point` 指派給 Tuple 來擷取個別的欄位：

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

當您初始化元組時，所使用的變數會與您想要用於元組專案的名稱相同：可從用來初始化元組的變數推斷元組元素的名稱：

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

您可以在「 [元組類型](../language-reference/builtin-types/value-tuples.md) 」一文中深入瞭解這項功能。

通常在您解構元組或以 `out` 參數呼叫方法時，會強制您要定義變數，而您無須在意變數的值也沒有使用該值的打算。 C# 新增了對 *捨棄* 的支援，來應付這種狀況。 捨棄是僅限寫入的變數，其名稱為 `_` (底線字元)；您可將所有想要捨棄的值指派到單一變數。 捨棄類似於未經指派的變數；和指派陳述式一樣，都不能用於程式碼中。

下列情況中支援捨棄：

- 解構元組或使用者定義型別時。
- 以 [out](../language-reference/keywords/out-parameter-modifier.md) 參數呼叫方法時。
- 執行 [is](../language-reference/keywords/is.md) 及 [switch](../language-reference/keywords/switch.md) 陳述式的模式比對作業時。
- 作為獨立識別項，當您想要將指派的值明確識別為捨棄時。

下列範例定義的 `QueryCityDataForYears` 方法，會傳回包含兩個不同年份之城市資料的 6 元組。 範例中的方法呼叫只有對方法傳回的兩個母體有效，所以會在解構元組時，將元組中剩餘的值視作捨棄處理。

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

如需詳細資訊，請參閱[捨棄](../discards.md)。

## <a name="pattern-matching"></a>模式比對

*模式* 比對是一組功能，可讓您在程式碼中以新的方式表示控制流程。 您可以針對其類型、值或其屬性的值來測試變數。 這些技術可建立更容易閱讀的程式碼流程。

模式比對支援 `is` 運算式和 `switch` 運算式。 每個都讓您能檢查物件和其屬性，以判斷該物件是否符合搜尋的模式。 您使用 `when` 關鍵字來指定其他規則給該模式。

`is`模式運算式會擴充熟悉的[ `is` 運算子](../language-reference/keywords/is.md#pattern-matching-with-is)，以查詢其類型的物件，並在一個指令中指派結果。 下列程式碼會檢查變數是否為 `int`，如果是，則將其加入至目前的總和：

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

從 C# 7.1 開始，`is` 和 `switch` 型別模式的模式運算式可能會有泛型型別參數的型別。 在檢查可能是 `struct` 或 `class` 型別的型別，以及您想要避免 boxing 時，這可能非常有用。

您可以在 [C# 中的模式比對](../pattern-matching.md)中深入了解模式比對。

## <a name="async-main"></a>非同步主要

「非同步主要」方法可讓您在 `Main` 方法中使用 `await`。 在過去您必須這樣寫：

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

現在您可以這樣寫：

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

如果您的程式不會傳回結束代碼，您可以宣告傳回 <xref:System.Threading.Tasks.Task> 的 `Main` 方法：

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

您可以在程式設計指南的[非同步主要](../programming-guide/main-and-command-args/index.md)文章中閱讀更多詳細資料。

## <a name="local-functions"></a>區域函式

類別的許多設計都包括從唯一一個位置呼叫的方法。 這些額外的私用方法會使每一種方法維持小而聚焦。 「區域函式」可讓您在另一個方法的內容中宣告方法。 區域函式可讓類別讀者輕鬆查看區域方法只會從其宣告的內容中呼叫。

有兩個常見的區域函式使用案例︰公用迭代器方法和公用非同步方法。 這兩種方法都會產生程式碼，比程式設計人員想像更晚才報告錯誤。 在迭代器方法中，任何例外狀況只會在呼叫列舉傳回序列的程式碼時觀察到。 在非同步方法中，任何例外狀況只會在傳回的 `Task` 等候時觀察到。 下列範例示範使用區域函式分隔參數驗證和迭代器實作：

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

相同的技巧也可以運用在 `async` 方法，以確保在非同步工作開始之前，會擲回引數驗證所引發的例外狀況︰

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

現在支援此語法：

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

屬性 `SomeThingAboutFieldAttribute` 套用至編譯器針對 `SomeProperty` 產生的支援欄位。 如需詳細資訊，請參閱 C# 程式設計指南中的[屬性](../programming-guide/concepts/attributes/index.md)。

> [!NOTE]
> 某些區域函數所支援的設計也可以使用 *lambda 運算式* 來完成。 如需詳細資訊，請參閱 [區域函數與 lambda 運算式](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)。

## <a name="more-expression-bodied-members"></a>更多運算式主體成員

C # 6 引進了成員函式和唯讀屬性的運算式主體成員。 C# 7.0 擴充了可以實作為運算式的允許成員。 在 C# 7.0 中，您可以實作「建構函式」、「完成項」，以及「屬性」和「索引子」上的 `get` 和 `set` 存取子。 下列程式碼將示範各項的範例：

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> 這個範例不需要完成項，但仍加以顯示以示範語法。 除非為釋放 Unmanaged 資源所需，否則不應該在類別中實作完成項。 您也應該考慮使用 <xref:System.Runtime.InteropServices.SafeHandle> 類別而不是直接管理 Unmanaged 資源。

這些運算式主體成員的新位置代表 C# 語言的重要里程碑︰這些功能是由參與開放原始碼 [Roslyn](https://github.com/dotnet/Roslyn) 專案的社群成員所實作。

將方法變更為運算式主體成員是[二進位相容](version-update-considerations.md#binary-compatible-changes)變更。

## <a name="throw-expressions"></a>throw 運算式

在 C# 中，`throw` 一直都是陳述式。 因為 `throw` 是陳述式，而不是運算式，所以有您無法在其中使用它的 C# 建構。 這些包含條件運算式、Null 聯合運算式和一些 Lambda 運算式。 新增運算式主體成員會新增 `throw` 運算式適用的更多位置。 您可以撰寫任何這些結構，c # 7.0 引進了 [*擲回運算式*](../language-reference/keywords/throw.md#the-throw-expression)。

此新增可讓您更輕鬆地撰寫更多以運算式為基礎的程式碼。 您不需要額外的陳述式就可以進行錯誤檢查。

## <a name="default-literal-expressions"></a>預設常值運算式

預設常值運算式是預設值運算式的增強功能。 這些運算式會將變數初始化為預設值。 在過去您必須這樣寫：

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

您現在可以略過初始化右側的類型：

```csharp
Func<string, bool> whereClause = default;
```

如需詳細資訊，請參閱[預設運算子](../language-reference/operators/default.md)一文中的[預設常值](../language-reference/operators/default.md#default-literal)一節。

## <a name="numeric-literal-syntax-improvements"></a>數值常值的語法增強功能

錯譯數值常數，可能會使得在第一次閱讀它時，更加難以了解程式碼。 位元遮罩或其他符號值容易遭到誤解。 C# 7.0 包含兩項新功能，可以用預期用途最容易閱讀的方式來撰寫數字︰「二進位常值」和「數字分隔符號」。

當您在建立位元遮罩時，或是每當數字的二進位表示法構成最容易閱讀的程式碼時，請以二進位撰寫該數字︰

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

常數開頭的 `0b` 表示數字是撰寫為二進位數字。 二進位數可能會很長，因此藉由將作為數位分隔符號來查看位模式通常會更容易 `_` ，如上述範例中的二進位常數所示。 千位分隔符號可以出現在常數的任何位置。 若是以10為底數的數位，通常會使用它作為千位分隔符號。 十六進位和二進位數值常值的開頭可能是 `_` ：

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

千位分隔符號也可以搭配 `decimal`、`float` 和 `double` 類型使用︰

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

結合起來，您在宣告數值常數時可以有更多的可讀性。

## <a name="out-variables"></a>`out` 變數

`out`在 c # 7 中已改善支援參數的現有語法。 您現在可以在方法呼叫的引數清單中宣告 `out` 變數，而不是撰寫個別的宣告陳述式︰

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

您可能會想要明確指定變數的類型 `out` ，如上述範例所示。 不過，語言有支援使用隱含型別區域變數︰

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- 程式碼更容易閱讀與理解。
  - 您可以在使用時宣告 out 變數，而不是在先前的程式程式碼上。
- 不需要指派初始值。
  - 藉由在方法呼叫中使用所在宣告 `out` 變數，就不會在指派它之前意外使用它。

加入 C# 7.0 中以允許 `out` 變數宣告的語法已經擴充，以包含欄位初始設定式、屬性初始設定式、建構函式初始設定式和查詢子句。 它讓您能執行如下列範例的程式碼：

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

## <a name="non-trailing-named-arguments"></a>非後置具名引數

當具名引數位於正確位置時，方法呼叫現在可以在位置引數前面使用具名引數。 如需詳細資訊，請參閱 [指名的和選擇性引數](../programming-guide/classes-and-structs/named-and-optional-arguments.md)。

## <a name="private-protected-access-modifier"></a>*private protected* 存取修飾詞

新的複合存取修飾詞：`private protected` 指出可藉由包含類別或在相同組件中宣告的衍生類別來存取成員。 `protected internal` 允許衍生類別或相同組件中的類別進行存取，而 `private protected` 則限制在相同組件中宣告的衍生類型進行存取。

如需詳細資訊，請參閱語言參考中的 [存取](../language-reference/keywords/access-modifiers.md) 修飾詞。

## <a name="improved-overload-candidates"></a>改進的多載候選項目

在每個版本中，多載解析規則都會更新，以解決模稜兩可的方法引動過程具有「明確」選項的情況。 此版本新增三個新的規則，以協助編譯器挑選明確的選項：

1. 當方法群組同時包含執行個體和靜態成員時，如果在沒有執行個體接收者或內容的情況下叫用方法，編譯器會捨棄執行個體成員。 如果使用執行個體接收者叫用方法，編譯器就會捨棄靜態成員。 沒有接收者時，編譯器只會在靜態內容中包含靜態成員，否則將同時包含靜態成員和執行個體成員。 當無法確定接收者是執行個體或型別時，編譯器會包含兩者。 無法使用隱含 `this` 執行個體接收者的靜態內容，包括未定義 `this` 的成員主體 (例如靜態成員)，以及不能使用 `this` 的位置 (例如欄位初始設定式和建構函式初始設定式)。
1. 當方法群組包含某些型別引數不滿足其限制式的泛型方法時，這些成員將會從候選集合中移除。
1. 針對方法群組轉換，其傳回型別與委派的傳回型別不符合的候選方法，將會從集合中移除。

您只會注意到此變更，因為若確定何種方法較佳，就會發現模稜兩可的方法多載會有較少的編譯器錯誤。

## <a name="enabling-more-efficient-safe-code"></a>啟用更有效率的安全的程式碼

您應該能夠安全地撰寫與不安全的程式碼一樣高效能的 C# 程式碼。 安全的程式碼可避免一些錯誤類別，例如緩衝區溢位、偏離的指標和其他記憶體存取錯誤。 這些新功能擴充了可驗證安全的程式碼的功能。 儘可能使用安全的建構來撰寫更多的程式碼。 這些功能都讓這變得更容易。

下列新功能針對安全的程式碼支援較佳效能的佈景主題：

- 您可以在不釘選的情況下存取固定的欄位。
- 您可以重新指派 `ref` 區域變數。
- 您可以在 `stackalloc` 陣列上使用初始設定式。
- 您可以搭配支援模式的任何型別使用 `fixed` 陳述式。
- 您可以使用其他的泛型限制式。
- 參數上的 `in` 修飾詞，可指定引數將以傳址方式傳遞，但不受呼叫的方法修改。 將 `in` 修飾詞新增至引數是[來源相容變更](version-update-considerations.md#source-compatible-changes)。
- 方法上 `ref readonly` 修飾詞的傳回內容，可指示方法要以傳址方式傳回其值，但不允許寫入該物件。 如果將傳回項目指派給值。則新增 `ref readonly` 修飾詞是[來源相容變更](version-update-considerations.md#source-compatible-changes)。 將 `readonly` 修飾詞新增至現有 `ref` 傳回陳述式是[不相容的變更](version-update-considerations.md#incompatible-changes)。 需要呼叫端更新 `ref` 本機變數的宣告，以包含 `readonly` 修飾詞。
- `readonly struct` 宣告，可指示結構會固定，且應以 `in` 參數傳遞至其成員方法。 將 `readonly` 修飾詞新增至現有 struct 宣告是[二進位相容變更](version-update-considerations.md#binary-compatible-changes)。
- `ref struct` 宣告，可指示結構類型會直接存取受控記憶體，且一律會配置堆疊。 將 `ref` 修飾詞新增至現有 `struct` 宣告是[不相容的變更](version-update-considerations.md#incompatible-changes)。 `ref struct` 不能是類別的成員，或用於可能會在堆積上配置的其他位置。

您可以在[撰寫安全、有效率的程式碼](../write-safe-efficient-code.md)深入了解這些變更。

### <a name="ref-locals-and-returns"></a>Ref 區域變數和傳回

這項功能可以啟用使用和傳回在其他地方定義之變數參考的演算法。 其中一個範例是使用大型矩陣，並尋找具有特定特性的單一位置。 下列方法會傳回矩陣中該儲存體的 **參考**：

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

現在，`ref` 區域變數可能會在初始化之後被重新指派，以參照不同的執行個體。 下列程式碼現在會編譯：

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

如需詳細資訊，請參閱有關傳回的[ `ref` 和 `ref` 區域變數](../programming-guide/classes-and-structs/ref-returns.md)的文章，以及的相關文章 [`foreach`](../language-reference/keywords/foreach-in.md) 。

如需詳細資訊，請參閱 [ref 關鍵字](../language-reference/keywords/ref.md)一文。

### <a name="conditional-ref-expressions"></a>`ref` 條件運算式

最後，條件運算式可能會產生參考結果，而不是實值結果。 例如，您可以撰寫下列程式碼，在兩個陣列的其中一個上，擷取對第一個元素的參考：

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

變數 `r` 是 `arr` 或 `otherArr` 中對第一個值的參考。

如需詳細資訊，請參閱語言參考中的[條件運算子 (?:)](../language-reference/operators/conditional-operator.md)。

### <a name="in-parameter-modifier"></a>`in` 參數修飾詞

`in`關鍵字會補充現有的 ref 和 out 關鍵字，以傳址方式傳遞引數。 `in` 關鍵字會指定以參考型式傳遞引數，但呼叫的方法不會修改值。

您可以宣告以傳值方式或唯讀參考傳遞的多載，如下列程式碼所示：

```csharp
static void M(S arg);
static void M(in S arg);
```

前一個範例中的 by 值 (先) 多載比唯讀參考版本更好。 若要呼叫具有唯讀參考引數的版本，您呼叫方法時必須包含 `in` 修飾詞。

如需詳細資訊，請參閱[ `in` 參數修飾](../language-reference/keywords/in-parameter-modifier.md)詞上的文章。

### <a name="more-types-support-the-fixed-statement"></a>更多型別支援 `fixed` 陳述式

`fixed` 陳述式支援一組有限的型別。 從 C# 7.3 開始，包含傳回 `ref T` 或 `ref readonly T` 之 `GetPinnableReference()` 方法的任何型別都可能是 `fixed`。 新增此功能表示 `fixed` 可以與 <xref:System.Span%601?displayProperty=nameWithType> 和相關型別一起使用。

如需詳細資訊，請參閱語言參考中的[ `fixed` 語句](../language-reference/keywords/fixed-statement.md)文章。

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>索引 `fixed` 欄位不需要釘選

請考量此建構：

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

在舊版的 C# 中，您需要釘選變數，才能存取屬於 `myFixedField` 的其中一個整數。 現在，下列程式碼會進行編譯而不將變數 `p` 固定在個別的 `fixed` 陳述式內：

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

變數 `p` 會存取 `myFixedField` 中的一個元素。 您不需要宣告個別的 `int*` 變數。 您仍然需要 `unsafe` 內容。 在舊版的 C# 中，您需要宣告第二個固定指標：

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

如需詳細資訊，請參閱有關[ `fixed` 語句](../language-reference/keywords/fixed-statement.md)的文章。

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc` 陣列支援初始設定式

您可以在初始化陣列時，指定陣列中元素的值：

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

現在，相同的語法可以套用至使用 `stackalloc` 宣告的陣列：

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

如需詳細資訊，請參閱[ `stackalloc` 操作員](../language-reference/operators/stackalloc.md)文章。

### <a name="enhanced-generic-constraints"></a>增強泛型限制式

您現在可以指定型別 <xref:System.Enum?displayProperty=nameWithType> 或 <xref:System.Delegate?displayProperty=nameWithType> 作為型別參數的基底類別限制式。

您也可以使用新的 `unmanaged` 條件約束，指定型別參數必須是不可為 null 的 [非受控型](../language-reference/builtin-types/unmanaged-types.md)別。

如需詳細資訊，請參閱[ `where` 泛型條件約束](../language-reference/keywords/where-generic-type-constraint.md)的相關文章和[類型參數的條件約束](../programming-guide/generics/constraints-on-type-parameters.md)。

將這些條件約束新增至現有型別是[不相容變更](version-update-considerations.md#incompatible-changes)。 封閉式泛型型別可能不再符合這些新的條件約束。

### <a name="generalized-async-return-types"></a>通用的非同步傳回型別

從非同步方法傳回 `Task` 物件可能會造成在特定路徑的效能瓶頸。 `Task` 是參考型別，因此使用它表示要配置物件。 當使用 `async` 修飾詞宣告的方法傳回快取的結果時，或是以同步方式完成，額外配置可能會在效能關鍵的程式碼區段中變成一項重要的時間成本。 如果這些配置發生在緊密迴圈中，它可能會變得成本很高。

新的語言功能表示 async 方法傳回型別不限於 `Task`、`Task<T>` 和 `void`。 傳回的型別仍然必須滿足非同步模式，也就是表示 `GetAwaiter` 方法必須可存取。 作為一個具體的範例， `ValueTask` 類型已新增至 .net 以利用這個新的語言功能：

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> 您需要新增 NuGet 套件 >，才能 [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) 使用 <xref:System.Threading.Tasks.ValueTask%601> 類型。

這項增強功能最能幫助程式庫作者避免在效能關鍵的程式碼中配置 `Task`。

## <a name="new-compiler-options"></a>新的編譯器選項

新的編譯器選項支援 C# 程式的新組建和 DevOps 案例。

### <a name="reference-assembly-generation"></a>參考組件產生

有兩個新編譯器選項會產生「僅參考的組件」：[-refout](../language-reference/compiler-options/refout-compiler-option.md) 和 [-refonly](../language-reference/compiler-options/refonly-compiler-option.md)。
連結的文章將更詳細地說明這些選項和參考組件。

### <a name="public-or-open-source-signing"></a>公用或開放原始碼簽署

`-publicsign` 編譯器選項會指示編譯器使用公開金鑰簽署組件。 該組件標示為已簽署，但簽章取自公開金鑰。 此選項可讓您使用公開金鑰，從開放原始碼專案建置簽署的組件。

如需詳細資訊，請參閱 [-publicsign 編譯器選項](../language-reference/compiler-options/publicsign-compiler-option.md)一文。

### <a name="pathmap"></a>pathmap

`-pathmap` 編譯器選項會指示編譯器使用對應的來源路徑取代建置環境的來源路徑。 `-pathmap` 選項控制編譯器寫入 PDB 檔案或 <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> 的來源路徑。

如需詳細資訊，請參閱 [-pathmap 編譯器選項](../language-reference/compiler-options/pathmap-compiler-option.md)一文。

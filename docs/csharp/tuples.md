---
title: Tuple 型別 - C# 手冊
description: 了解 C# 中的未具名和具名 Tuple 類型
ms.date: 05/15/2018
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: 5ef8d89f62a30d3d64f7377972e31d9c4d93d41e
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/18/2018
---
# <a name="c-tuple-types"></a>C# Tuple 型別 #

C# Tuple 是您使用輕量型語法所定義的型別。 優點包括更簡單的語法、以元素數目 (稱為基數) 與型別為依據的轉換規則，以及複本、相等測試與指派的一致性規則。 折衷方式是，Tuple 不支援與繼承建立關聯的一些物件導向慣用語。 您可以在 [C# 7.0 新功能中的 Tuple](whats-new/csharp-7.md#tuples) 文章的一節中取得概觀。

在本文章中，您將了解在 C# 7.0 及更新版本中控管 Tuple 的語言規則、不同的 Tuple 使用方式，以及使用 Tuple 的初始指導。

> [!NOTE]
> 新的 Tuple 功能需要 <xref:System.ValueTuple> 類型。
> 您必須新增 NuGet 套件 [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/)，以將它用於不包含類型的平台。
>
> 這類似於依賴架構中所傳遞類型的其他語言功能。 範例包含依賴 `INotifyCompletion` 介面的 `async` 和 `await` 以及依賴 `IEnumerable<T>` 的 LINQ。 不過，傳遞機制會變更，因為 .NET 變得與平台更為無關。 .NET Framework 可能不會永遠隨附於相同的步調，作為語言編譯器。 如果新語言功能依賴新類型，則在提供語言功能時，會以 NuGet 套件形式提供這些類型。 因為這些新類型會新增至 .NET Standard API 並傳遞為架構的一部分，所以將會移除 NuGet 套件需求。

讓我們開始了解新增 Tuple 支援的原因。 方法會傳回單一物件。 Tuple 可讓您更輕鬆地將多個值封裝在該單一物件中。

.NET Framework 已有泛型 `Tuple` 類別。 不過，這些類別有兩個主要限制。 其中一個限制是，`Tuple` 已將其屬性命名為 `Item1`、`Item2` 等等。 這些名稱未包含任何語意資訊。 使用這些 `Tuple` 類型無法表達各個屬性的意義。 而新的語言功能則可讓您為元組中的元素宣告及使用具有語意意義的名稱。

`Tuple` 類別會造成更多的效能考量，因為它們都是參考型別。 使用其中一個 `Tuple` 類型表示配置物件。 在最忙碌路徑上，配置許多小型物件可能會對您應用程式的效能造成可觀的衝擊。 因此，元組的語言支援會運用新的 `ValueTuple` 結構。

若要避免這些缺點，您可以建立 `class` 或 `struct` 來帶出多個元素。 不幸的是，您需要執行更多工作，並且會模糊您的設計目的。 設定 `struct` 或 `class` 表示您定義的類型同時具有資料和行為。 許多次，您都只想要將多個值儲存在單一物件中。

語言功能和 `ValueTuple` 泛型結構會強制執行您無法將任何行為 (方法) 新增至這些 Tuple 類型的規則。
所有 `ValueTuple` 類型都是「可變動結構」。 每個成員欄位都是公用欄位。 這可將它們設為非常輕量型。 不過，這表示，如果不變性十分重要，則不應該使用 Tuple。

Tuple 是比 `class` 和 `struct` 類型更為簡單且更具彈性的資料容器。 讓我們來探索這些差異。

## <a name="named-and-unnamed-tuples"></a>具名和未具名 Tuple

`ValueTuple` 結構具有名為 `Item1`、`Item2`、`Item3` 等等的欄位，而這些欄位與現有 `Tuple` 型別中所定義的屬性類似。
這些名稱只是您可用於「未具名 Tuple」的名稱。 當您未將任何替代欄位名稱提供給 Tuple 時，即已建立未具名 Tuple：

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

上述範例中使用了常值常數將 Tuple 初始化，且不會有在 C# 7.1 中使用「Tuple 欄位名稱投射轉換」建立的元素名稱。

不過，當您初始化 Tuple 時，可以使用新的語言功能，讓每個欄位具有更適合的名稱。 這麼做會建立「具名 Tuple」。
具名元組仍會有名為 `Item1`、`Item2`、`Item3` 等等的元素。
但對於您已命名的任一元素，也會有同義字。
您可以指定每個元素的名稱來建立具名元組。 其中一個方式是在 Tuple 初始化期間指定名稱：

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#02_NamedTuple "Named tuple")]

這些同義字是由編譯器和語言所處理，讓您可以有效率地使用具名 Tuple。 IDE 和編輯器可以使用 Roslyn API 來讀取這些語意名稱。 您可以在相同組件的任何地方，依據這些語意名稱來參考具名 Tuple 的元素。 產生所編譯的輸出時，編譯器會將您定義的名稱取代為 `Item*` 對等項目。 編譯過的 Microsoft Intermediate Language (MSIL) 不會包括您為這些元素指定的名稱。

從 C# 7.1 開始，元組的欄位名稱可從用來將元組初始化的變數提供。 即為**[元組投影初始設定式](#tuple-projection-initializers)**。 下列程式碼會建立名為 `accumulation` 的元組，並有元素 `count` (整數) 與 `sum` (雙精度浮點數)。

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectedTupleNames "Named tuple")]

編譯器必須知道您針對從公用方法或屬性傳回之 Tuple 所建立的名稱。 在這些情況下，編譯器會在方法上新增 <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> 屬性。 這個屬性包含 <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> 清單屬性，其中包含為 Tuple 中各元素指定的名稱。

> [!NOTE]
> Visual Studio 這類開發工具也會讀取該中繼資料，並使用中繼資料欄位名稱來提供 IntelliSense 和其他功能。

請務必了解新 Tuple 的這些基礎基本項目和 `ValueTuple` 類型，以了解將具名 Tuple 指派給彼此的規則。

## <a name="tuple-projection-initializers"></a>元組投影初始設定式

一般來說，元組投影初始設定式會使用元組初始化陳述式右手邊的變數或欄位名稱來運作。
如有指定明確名稱，則會優先於任何投影名稱。 例如，在下列初始設定式中，元素為 `explicitFieldOne` 與 `explicitFieldTwo`，而非 `localVariableOne` 與 `localVariableTwo`：

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

對於未提供明確名稱的任何欄位，會投影適用的隱含名稱。 您不需要明確或隱含地提供語意名稱。 下列初始設定式會有值為 `42` 的欄位名稱 `Item1`，以及值為 "The answer to everything" 的欄位名稱 `StringContent`：

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#MixedTuple "mixed tuple")]

在兩種情況下，候選欄位名稱不會投影至元組欄位：

1. 候選名稱是保留的元組名稱。 範例包括 `Item3`、`ToString`， 或 `Rest`。
1. 候選名稱與另一個明確或隱含的元組欄位名稱重複。

這些情況可避免語意模糊。 如果將這些名稱作為元組中的欄位名稱使用，就會造成語意模糊。 這兩種情況都不會造成編譯時期錯誤。 反之，沒有投影名稱的元素不會有語意名稱對其投影。  下列範例將示範這些情況：

[!code-csharp[Ambiguity](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

這些情況不會造成編譯器錯誤，因為這使用 C# 7.0 撰寫的程式碼而言會是重大變更，而當時元組欄位名稱投影還無法使用。

## <a name="equality-and-tuples"></a>相等和 Tuple

從 C# 7.3 開始，Tuple 型別支援 `==` 和 `!=` 運算子。 這些運算子的運作方式，是透過依順序比較左側引數的每個成員與右側引數的每個成員。 這些比較會進行最少運算。 只要有一組不相等，`==` 運算子就會停止評估成員。 只要有一組相等，`!=` 運算子就會停止評估成員。 下列程式碼範例使用 `==`，但比較規則均適用於 `!=`。 下列程式碼範例顯示了兩組整數的相等比較：

[!code-csharp[TupleEquality](../../samples/snippets/csharp/tuples/tuples/program.cs#Equality "Testing tuples for equality")]

有數個規則讓 tuple 相等測試更加方便。 如果其中一個 Tuple 是可為 null 的 Tuple，則 Tuple 相等會執行[提升轉換](/dotnet/csharp/language-reference/language-specification/conversions.md#lifted-conversion-operators)，如下列程式碼所示：

[!code-csharp[NullableTupleEquality](../../samples/snippets/csharp/tuples/tuples/program.cs#NullableEquality "Comparing Tuples and nullable tuples")]

Tuple 相等也會對這兩個 Tuple 的每個成員執行隱含轉換。 其中包括提升轉換、擴展轉換或其他的隱含轉換。 下列範例顯示，由於從整數到長整數的隱含轉換，整數 2-tuple 可以與長整數 2-tuple 進行比較：

[!code-csharp[SnippetMemberConversions](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetMemberConversions "converting tuples for equality tests")]

Tuple 成員的名稱不會參與相等測試。 不過，如果其中一個運算元是具有明確名稱的 Tuple 常值，則編譯器會產生警告 CS8383，前提是這些名稱與另一個運算元的名稱不相符。
在兩個運算元都是 Tuple 常值的情況下，警告會在右邊的運算元上，如下列範例所示：

[!code-csharp[MemberNames](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetMemberNames "Tuple member names do not participate in equality tests")]

最後，Tuple 可能包含巢狀 Tuple。 Tuple 相等會透過巢狀 Tuple 比較每個運算元的「圖形」，如下列範例所示：

[!code-csharp[NestedTuples](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetNestedTuples "Tuples may contain nested tuples that participate in tuple equality.")]

## <a name="assignment-and-tuples"></a>指派和 Tuple

該語言支援具有相同元素數目之 Tuple 型別之間的指派，其中右側的每個元素可以隱含地轉換成其對應的左側元素。 不會考慮對指派進行其他轉換。 讓我們看看 Tuple 類型之間允許的指派類型。

請考慮在下列範例中使用的這些參數：

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/tuples/program.cs#03_VariableCreation "Variable creation")]

前兩個變數 `unnamed` 與 `anonymous` 都未提供元素的語意名稱。 欄位名稱為 `Item1` 和 `Item2`。
後兩個變數 `named` 與 `differentName` 皆有為元素指定的語意名稱。 這兩個 Tuple 有不同的元素名稱。

這四個元組全都有相同數目的元素 (稱為「基數」)，而且這些元素的類型完全相同。 因此，所有這些指派都會運作︰

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/tuples/program.cs#04_VariableAssignment "Variable assignment")]

請注意，不會指派 Tuple 的名稱。 元素的值會依照元組中的元素順序指派。

類型或元素數目不同的元組則無法指派：

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Tuple 作為方法傳回值

其中一個最常見的 Tuple 用法是作為方法傳回值。 讓我們逐步解說一個範例。 請考慮使用這個計算一系列數字標準差的方法︰

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> 這些範例會計算未修正的樣本標準差。
> 更正的範例標準差公式會將與平均值的平方差總和除以 (N-1)，而非 N，就像 `Average` 擴充方法一樣。 如需標準差的這些公式之差異的詳細資料，請參閱統計文字。

上述程式碼會遵循標準差的文字方塊公式。 它會產生正確答案，但這是沒有效率的實作。 這個方法會列舉序列兩次︰一次是產生平均值，一次是產生平均值差之平方的平均值。
(請記住，LINQ 查詢會變慢，因此，計算與平均值的差異以及這些差異的平均值只會建立一個列舉)。

有替代公式可以只使用該序列的一個列舉來計算標準差。  此計算會產生兩個值，因為它會列舉序列︰序列中所有項目的總和，以及每個值平方的總和︰

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

此版本只會列舉序列一次。 但是它不是可重複使用的程式碼。 繼續工作時，會發現許多不同的統計運算使用序列中的項目數、序列總和，以及序列平方總和。 讓我們重構這個方法，並撰寫可產生所有這三個值的公用程式方法。 所有這三個值都可以作為 Tuple 傳回。

讓我們更新這個方法，因此在列舉期間計算的三個值會儲存在 Tuple 中。 這會建立這個版本：

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

Visual Studio 的重構支援可輕鬆地將核心統計資料的功能擷取至私用方法。 這會提供 `private static` 方法，以傳回具有 `Sum`、`SumOfSquares` 和 `Count` 這三個值的 Tuple 類型：

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]
 
如果您想要手動進行一些快速編輯，則語言會啟用可讓您使用的更多選項。 首先，您可以使用 `var` 宣告來初始化 `ComputeSumAndSumOfSquares` 方法呼叫的 Tuple 結果。 您也可以在 `ComputeSumAndSumOfSquares` 方法內建立三個不連續變數。 最終版本如下列程式碼所示：

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

這個最終版本可以用於任何需要這三個值的方法或其任何子集。

語言支援其他選項來管理這些元組傳回方法中的元素名稱。

您可以從傳回值宣告中移除欄位名稱，並傳回未具名 Tuple：

```csharp
private static (double, double, int) ComputeSumAndSumOfSquares(IEnumerable<double> sequence)
{
    double sum = 0;
    double sumOfSquares = 0;
    int count = 0;

    foreach (var item in sequence)
    {
        count++;
        sum += item;
        sumOfSquares += item * item;
    }

    return (sum, sumOfSquares, count);
}
```

這個 Tuple 的欄位會命名為 `Item1`、`Item2` 和 `Item3`。
建議您為方法中傳回的元組元素提供語意名稱。

Tuple 很有用的另一個習慣用法是當您撰寫 LINQ 查詢時。 最終投射結果通常包含所選取物件的部分屬性，但不是全部屬性。

您傳統上會將查詢結果投影至具有匿名型別的一系列物件。 這有許多限制，主要是因為無法在方法的傳回型別中方便地命名匿名型別。 使用 `object` 或 `dynamic` 作為結果類型的替代方式，其效果成本相當可觀。

傳回一系列的元組類型十分簡單，而且在編譯時間以及透過 IDE 工具都可以使用元素的名稱和類型。
例如，請考慮使用 ToDo 應用程式。 您可以定義與下面類似的類別，以代表 ToDo 清單中的單一項目︰

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

行動應用程式可能支援只顯示標題之目前 ToDo 項目的壓縮格式。 該 LINQ 查詢會建立只包含識別碼和標題的投影。 傳回一系列 Tuple 的方法表示該設計良好︰

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> 在 C# 7.1 中，元組投影可讓您使用元素建立具名元組，方式與匿名型別中的屬性命名相似。 在上述的程式碼中，查詢投影的 `select` 陳述式會建立具有元素 `ID` 與 `Title` 的元組。

具名 Tuple 可以是簽章的一部分。 它可讓編譯器和 IDE 工具提供您正確使用結果的靜態檢查。 具名 Tuple 也帶有靜態類型資訊，因此不需要使用昂貴的執行階段功能，例如使用結果的反射或動態繫結。

## <a name="deconstruction"></a>解構

您可以「解構」方法所傳回的 Tuple，來解除封裝 Tuple 中的所有項目。 有三種不同的方法可以解構 Tuple。  首先，您可以在括弧內明確宣告每個欄位的類型，以建立元組中每個元素的離散變數：

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

您可以在括弧外部使用 `var` 關鍵字，以宣告 Tuple 中每個欄位的隱含類型變數︰

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

它也可以搭配使用 `var` 關鍵字與括弧內的任何或所有變數宣告。 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

您無法在括弧外部使用特定型別，即使 Tuple 中的每個欄位都有相同的型別也是一樣。

您可以解構 Tuple 以及現有宣告：

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
>  您不能混用現有宣告與括弧內的宣告。 例如，不允許使用下列項目：`(var x, y) = MyMethod();`。 這會產生錯誤 CS8184，因為 *x* 是在括弧內宣告，而 *y* 先前已在其他位置宣告。

### <a name="deconstructing-user-defined-types"></a>解構使用者定義型別

任何 Tuple 類型都可以如上進行解構。 也很容易在任何使用者定義型別 (類別、結構，甚至是介面) 上啟用解構。

類型作者可以定義一或多個 `Deconstruct` 方法，以將值指派給任意數目的 `out` 變數，而變數代表構成類型的資料項目。 例如，下列 `Person` 類型會定義 `Deconstruct` 方法，以將人員物件解構為代表名字和姓氏的元素：

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

解構方法會啟用從 `Person` 到兩個字串的指派，而這兩個字串代表 `FirstName` 和 `LastName` 屬性：

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

您甚至可以針對不是由您撰寫的類型啟用解構。
`Deconstruct` 方法可以是解除封裝物件的可存取資料成員的擴充方法。 下列範例示範衍生自 `Person` 型別的 `Student` 型別，以及將 `Student` 解構為三個變數的擴充方法，而這三個變數代表 `FirstName`、`LastName` 和 `GPA`：

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

`Student` 物件現在有兩個可存取的 `Deconstruct` 方法︰針對 `Student` 類型所宣告的擴充方法，以及 `Person` 類型的成員。 兩者都在範圍內，並可將 `Student` 解構為兩個或三個變數。
如果您將一位學生指派給三個變數，則都會傳回名字、姓氏和 GPA。 如果您將一位學生指派給兩個變數，則只會傳回名字和姓氏。

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

定義類別或類別階層中的多個 `Deconstruct` 方法時必須特別小心。 `out` 參數數目相同的多個 `Deconstruct` 方法可能會快速地造成模稜兩可。 呼叫端可能無法輕鬆地呼叫所需的 `Deconstruct` 方法。

在此範例中，模稜兩可呼叫的機率最小，因為 `Person` 的 `Deconstruct` 方法有兩個輸出參數，而 `Student` 的 `Deconstruct` 方法則有三個。

解構運算子不會參與相等測試。 下列範例會產生編譯器錯誤 CS0019：

```csharp
Person p = new Person("Althea", "Goodwin");
if (("Althea", "Goodwin") == p)
    Console.WriteLine(p);
```

`Deconstruct` 方法可以將 `Person` 物件 `p` 轉換為包含兩個字串的 Tuple，但它並不適用於相等測試的內容中。

## <a name="conclusion"></a>結論 

具名元組的新語言和程式庫支援可讓您更輕鬆地處理使用可儲存多個元素的資料結構但未定義行為的設計，就像類別與結構一樣。 將 Tuple 用於這些類型十分簡單且簡潔。 您會獲得靜態類型檢查的所有優點，而不需要使用更詳細的 `class` 或 `struct` 語法來撰寫類型。 即便如此，它們還是最適用於為 `private` 或 `internal` 的公用程式方法。 公用方法傳回具有多個元素的值時，請建立使用者定義型別，即 `class` 或 `struct` 型別。

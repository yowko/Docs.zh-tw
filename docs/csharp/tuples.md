---
title: "Tuple | C# 手冊"
description: "了解 C 中的未具名和具名 Tuple 類型#"
keywords: .NET, .NET Core, C#
author: BillWagner
ms-author: wiwagn
ms.date: 11/23/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f2c81b7e18f36bde5b46c0c6df5c8122cd303931
ms.lasthandoff: 03/13/2017

---

# <a name="c-tuple-types"></a>C# Tuple 類型 #

C# Tuple 是您使用輕量型語法所定義的類型。 優點包括更簡單的語法、根據欄位數目 (稱為 "arity") 和類型的轉換規則，以及複製和指派的一致規則。 折衷方式是，Tuple 不支援與繼承建立關聯的一些物件導向慣用語。 您可以在 [C# 7 之新功能中的 Tuple](csharp-7.md#tuples) 主題的一節中取得概觀。

在本主題中，您將了解在 C# 7 中控管 Tuple 的語言規則、不同的 Tuple 使用方式，以及使用 Tuple 的初始指導。

> [!NOTE]
> 新的 Tuple 功能需要 `System.ValueTuple` 類型。 在 Visual Studio 2017 中，您必須新增可在 NuGet 資源庫中取得的 NuGet 套件 [System.ValueTuple](https://www.nuget.org/packages/System.ValueTuple/)。
> 如果未使用這個套件，您可能會收到與 `error CS8179: Predefined type 'System.ValueTuple``2' is not defined or imported` 或 `error CS8137: Cannot define a class or member that utilizes tuples because the compiler required type 'System.Runtime.CompilerServices.TupleElementNamesAttribute' cannot be found.` 類似的編譯錯誤。

讓我們開始了解新增 Tuple 支援的原因。 方法會傳回單一物件。 Tuple 可讓您更輕鬆地將多個值封裝在該單一物件中。 

.NET Framework 已有泛型 `Tuple` 類別。 不過，這些類別有兩個主要限制。 其中一個限制是，`Tuple` 類別已命名其欄位 `Item1`、`Item2` 等等。 這些名稱未包含任何語意資訊。 使用這些 `Tuple` 類型並不會溝通每個欄位的意義。 另一個問題是 `Tuple` 類別為參考型別。 使用其中一個 `Tuple` 類型表示配置物件。 在最忙碌路徑上，這可能會對您應用程式的效能造成可觀的衝擊。

若要避免這些缺點，您可以建立 `class` 或 `struct` 以帶出多個欄位。 不幸的是，您需要執行更多工作，並且會模糊您的設計目的。 設定 `struct` 或 `class` 表示您定義的類型同時具有資料和行為。 許多次，您都只想要將多個值儲存在單一物件中。

Tuple 的新語言功能與架構中的一組新類別一起使用，可解決這些缺點。 這些新的 Tuple 使用新的 `ValueTuple` 泛型結構。 如名稱所示，此類型是 `struct`，而非 `class`。 這個結構有不同的版本，可支援具有不同數目的欄位的 Tuple。 新的語言支援提供 Tuple 類型之欄位的語意名稱，以及可更較鬆地建構或存取 Tuple 欄位的功能。

語言功能和 `ValueTuple` 泛型結構會強制執行您無法將任何行為 (方法) 新增至這些 Tuple 類型的規則。
所有 `ValueTuple` 類型都是「可變動結構」**。 每個成員欄位都是公用欄位。 這可將它們設為非常輕量型。 不過，這表示，如果不變性十分重要，則不應該使用 Tuple。

Tuple 是比 `class` 和 `struct` 類型更為簡單且更具彈性的資料容器。 讓我們來探索這些差異。

## <a name="named-and-unnamed-tuples"></a>具名和未具名 Tuple

`ValueTuple` 結構具有名為 `Item1`、`Item2`、`Item3` 等等的欄位，而這些欄位與現有 `Tuple` 類型中所定義的屬性類似。
這些名稱只是您可用於「未具名 Tuple」**的名稱。 當您未將任何替代欄位名稱提供給 Tuple 時，即已建立未具名 Tuple：

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#01_UnNamedTuple " Tuple")]

不過，當您初始化 Tuple 時，可以使用新的語言功能，讓每個欄位具有更適合的名稱。 這麼做會建立「具名 Tuple」**。
具名 Tuple 仍然會有名為 `Item1`、`Item2`、`Item3` 等等的欄位。
但它們也擁有任何具名欄位的同義字。
您可以指定每個欄位的名稱，以建立具名 Tuple。 其中一個方式是在 Tuple 初始化期間指定名稱：

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#02_NamedTuple "具名 Tuple")]

這些同義字是由編譯器和語言所處理，讓您可以有效率地使用具名 Tuple。 IDE 和編輯器可以使用 Roslyn API 來讀取這些語意名稱。 這可讓您依相同組件中任何位置的語意名稱來參考具名 Tuple 的欄位。 產生所編譯的輸出時，編譯器會將您定義的名稱取代為 `Item*` 對等項目。 編譯過的 Microsoft Intermediate Language (MSIL) 不會包括您為這些欄位所提供的名稱。 

編譯器必須知道您針對從公用方法或屬性傳回之 Tuple 所建立的名稱。 在這些情況下，編譯器會在方法上新增 `TupleElementNames` 屬性。 這個屬性包含 `TransformNames` 清單屬性，其中包含指定給 Tuple 中每個欄位的名稱。 

> [!NOTE]
> Visual Studio 這類開發工具也會讀取該中繼資料，並使用中繼資料欄位名稱來提供 IntelliSense 和其他功能。

請務必了解新 Tuple 的這些基礎基本項目和 `ValueTuple` 類型，以了解將具名 Tuple 指派給彼此的規則。

## <a name="assignment-and-tuples"></a>指派和 Tuple

語言支援在欄位數目相同且所有這些欄位都具有相同類型的 Tuple 類型間的指派。 這些類型必須是完全相同的編譯時期相符項目。 不會考慮對指派進行其他轉換。 讓我們看看 Tuple 類型之間允許的指派類型。

請考慮在下列範例中使用的這些參數：

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/tuples/program.cs#03_VariableCreation "變數建立")]

前兩個變數 (`unnamed` 和 `anonymous`) 未提供欄位的語意名稱。 欄位名稱為 `Item1` 和 `Item2`。
後兩個變數 (`named` 和 `differentName`) 已提供欄位的語意名稱。 請注意，這兩個 Tuple 有不同的欄位名稱。

所有這四個 Tuple 都有相同數目的欄位 (稱為 'arity')，而且這些欄位的類型完全相同。 因此，所有這些指派都會運作︰

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/tuples/program.cs#04_VariableAssignment "變數指派")]

請注意，不會指派 Tuple 的名稱。 依欄位在 Tuple 中的順序，指派欄位的值。

欄位類型或數目不同的 Tuple 無法進行指派：

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Tuple 作為方法傳回值

其中一個最常見的 Tuple 用法是作為方法傳回值。 讓我們逐步解說一個範例。 請考慮使用這個計算一系列數字標準差的方法︰

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/tuples/statistics.cs#05_StandardDeviation "計算標準差")]

> [!NOTE]
> 這些範例會計算未修正的樣本標準差。
> 更正的範例標準差公式會將與平均值的平方差總和除以 (N-1)，而非 N，就像 `Average` 擴充方法一樣。 如需標準差的這些公式之差異的詳細資料，請參閱統計文字。

這會遵循標準差的文字方塊公式。 它會產生正確答案，但這是十分沒有效率的實作。 這個方法會列舉序列兩次︰一次是產生平均值，一次是產生平均值差之平方的平均值。
(請記住，LINQ 查詢會變慢，因此，計算與平均值的差異以及這些差異的平均值只會建立一個列舉)。

有替代公式可以只使用該序列的一個列舉來計算標準差。  此計算會產生兩個值，因為它會列舉序列︰序列中所有項目的總和，以及每個值平方的總和︰

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/tuples/statistics.cs#06_SumOfSquaresFormula "使用平方總和計算標準差")]

版本只會列舉序列一次。 但是它不是容易重複使用的程式碼。 繼續工作時，會發現許多不同的統計運算使用序列中的項目數、序列總和，以及序列平方總和。 讓我們重構這個方法，並撰寫可產生所有這三個值的公用程式方法。

這是 Tuple 十分有用的位置。 

讓我們更新這個方法，因此在列舉期間計算的三個值會儲存在 Tuple 中。 這會建立這個版本：

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#07_TupleVersion "重構以使用 Tuple")]

Visual Studio 的重構支援可輕鬆地將核心統計資料的功能擷取至私用方法。 這會提供 `private static` 方法，以傳回具有 `Sum`、`SumOfSquares` 和 `Count` 這三個值的 Tuple 類型：

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#08_TupleMethodVersion "擷取公用程式方法之後")]
 
如果您想要手動進行一些快速編輯，則語言會啟用可讓您使用的更多選項。 首先，您可以使用 `var` 宣告來初始化 `ComputeSumAndSumOfSquares` 方法呼叫的 Tuple 結果。 您也可以在 `ComputeSumAndSumOfSquares` 方法內建立三個不連續變數。 最終版本如下︰

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#09_CleanedTupleVersion "最終清除之後")]

這個最終版本可以用於任何需要這三個值的方法或其任何子集。

語言支援其他選項來管理這些 Tuple 傳回方法中的欄位名稱。

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

您必須將此 Tuple 的欄位處理為 `Item1`、`Item2` 和 `Item3`。
建議您提供方法所傳回 Tuple 之欄位的語意名稱。

Tuple 可能十分有用的另一個慣用語是編寫 LINQ 查詢時，而在這類查詢中，最終結果為包含所選取物件的一些但非所有屬性的投影。

您傳統上會將查詢結果投影至具有匿名型別的一系列物件。 這有許多限制，主要是因為無法在方法的傳回型別中方便地命名匿名型別。 使用 `object` 或 `dynamic` 作為結果類型的替代方式，其效果成本相當可觀。

傳回一系列的 Tuple 類型十分簡單，而且在編譯時期以及透過 IDE 工具都可以使用欄位的名稱和類型。
例如，請考慮使用 ToDo 應用程式。 您可以定義與下面類似的類別，以代表 ToDo 清單中的單一項目︰

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#14_ToDoItem "待辦事項項目")]

行動應用程式可能支援只顯示標題之目前 ToDo 項目的壓縮格式。 該 LINQ 查詢會建立只包含識別碼和標題的投影。 傳回一系列 Tuple 的方法表示該設計良好︰

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#15_QueryReturningTuple "傳回 Tuple 的查詢")]

具名 Tuple 可以是簽章的一部分。 它可讓編譯器和 IDE 工具提供您正確使用結果的靜態檢查。 具名 Tuple 也帶有靜態類型資訊，因此不需要使用昂貴的執行階段功能，例如使用結果的反射或動態繫結。

## <a name="deconstruction"></a>解構

您可以「解構」**方法所傳回的 Tuple，來解除封裝 Tuple 中的所有項目。 有兩種不同的方法可以解構 Tuple。  首先，您可以在括弧內明確宣告每個欄位的類型，以建立 Tuple 中每個欄位的離散變數：

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

您可以在括弧外部使用 `var` 關鍵字，以宣告 Tuple 中每個欄位的隱含類型變數︰

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

它也可以搭配使用 `var` 關鍵字與括弧內的任何或所有變數宣告。 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```
請注意，您無法在括弧外部使用特定類型，即使 Tuple 中的每個欄位都有相同的類型也是一樣。

### <a name="deconstring-user-defined-types"></a>解構使用者定義型別

任何 Tuple 類型都可以如上進行解構。 也很容易在任何使用者定義型別 (類別、結構，甚至是介面) 上啟用解構。

類型作者可以定義一或多個 `Deconstruct` 方法，以將值指派給任意數目的 `out` 變數，而變數代表構成類型的資料項目。 例如，下列 `Person` 類型定義 `Deconstruct` 方法，以將人員物件解構為代表名字和姓氏的欄位：

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#12_TypeWithDeconstructMethod "具有解構方法的類型")]

解構方法會啟用從 `Person` 到兩個字串的指派，而這兩個字串代表 `FirstName` 和 `LastName` 屬性：

[!code-csharp[解構類型](../../samples/snippets/csharp/tuples/tuples/program.cs#12A_DeconstructType "解構類別類型")]

您甚至可以針對不是由您撰寫的類型啟用解構。
`Deconstruct` 方法可以是解除封裝物件的可存取資料成員的擴充方法。 下列範例示範衍生自 `Person` 類型的 `Student` 類型，以及將 `Student` 解構為三個變數的擴充方法，而這三個變數代表 `FirstName`、`LastName` 和 `GPA`：

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#13_ExtensionDeconstructMethod "具有解構擴充方法的類型")]

`Student` 物件現在有兩個可存取的 `Deconstruct` 方法︰針對 `Student` 類型所宣告的擴充方法，以及 `Person` 類型的成員。 兩者都在範圍內，並可將 `Student` 解構為兩個或三個變數。
如果您將一位學生指派給三個變數，則都會傳回名字、姓氏和 GPA。 如果您將一位學生指派給兩個變數，則只會傳回名字和姓氏。

[!code-csharp[解構擴充方法](../../samples/snippets/csharp/tuples/tuples/program.cs#13A_DeconstructExtension "使用擴充方法解構類別類型")]

定義類別或類別階層中的多個 `Deconstruct` 方法時必須十分小心。 `out` 參數數目相同的多個 `Deconstruct` 方法可能會快速地造成模稜兩可。 呼叫端可能無法輕鬆地呼叫所需的 `Deconstruct` 方法。

在此範例中，模稜兩可呼叫的機率最小，因為 `Person` 的 `Deconstruct` 方法有兩個輸出參數，而 `Student`的 `Deconstruct` 方法則有三個。

## <a name="conclusion"></a>結論 

具名 Tuple 的新語言和程式庫支援可讓您更輕鬆地處理使用可儲存多個欄位的資料結構但未定義行為的設計，就像類別和結構一樣。 將 Tuple 用於這些類型十分簡單且簡潔。 您會獲得靜態類型檢查的所有優點，而不需要使用更詳細的 `class` 或 `struct` 語法來撰寫類型。 即便如此，它們還是最適用於為 `private` 或 `internal` 的公用程式方法。 公用方法傳回具有多個欄位的值時，請建立使用者定義型別，即 `class` 或 `struct` 類型。


---
title: C# 6 的新功能 - C# 指南
description: 了解 C# 第 6 版的新功能
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: ad3515e1fc7d70e1377f007276c369d2884780f0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194029"
---
# <a name="whats-new-in-c-6"></a>C# 6 的新功能

C# 6.0 版包含許多功能，能提升開發人員的產能。 本版的功能包括︰

* [唯讀 Auto 屬性](#read-only-auto-properties)：
    - 您可以建立只能在建構函式中設定的唯讀 Auto 屬性。
* [Auto 屬性初始設定式](#auto-property-initializers)：
    - 您可以撰寫初始化運算式，以設定 Auto 屬性的初始值。
* [具有運算式主體的函式成員](#expression-bodied-function-members)：
    - 您可以使用 Lambda 運算式撰寫單行方法。
* [使用靜態](#using-static)：
    - 您可以將單一類別的所有方法都匯入目前的命名空間。
* [Null 條件運算子](#null-conditional-operators)：
    - 您可以精確且安全地存取物件的成員，同時仍然以 Null 條件運算子檢查 Null。
* [字串插補](#string-interpolation)：
    - 您可以使用內嵌運算式而非位置引數來撰寫字串格式化運算式。
* [例外狀況篩選條件](#exception-filters)：
    - 您可以根據例外狀況的屬性或其他程式狀態攔截運算式。 
* [`nameof` 運算式](#the-nameof-expression)：
    - 您可以讓編譯器產生符號的字串表示。
* [Catch 和 Finally 區塊中的 Await](#await-in-catch-and-finally-blocks)：
    - 您可以在先前不允許 `await` 運算式的位置中使用它們。
* [索引初始設定式](#index-initializers)：
    - 您可以撰寫關聯容器和序列容器的初始化運算式。
* [集合初始設定式的擴充方法](#extension-add-methods-in-collection-initializers)：
    - 集合初始設定式可以依賴可存取的擴充方法，以及成員方法。
* [改進的多載解析](#improved-overload-resolution)：
    - 有些建構先前會產生模稜兩可的方法呼叫，現在已可以正確解析。
* [`deterministic` 編譯器選項](#deterministic-compiler-output)：
    - deterministic 編譯器選項可確保相同來源的後續編譯會產生相同的二進位輸出。

這些功能的整體影響是您可撰寫更簡潔且更具可讀性的程式碼，。 語法包含許多常見做法的較少繁瑣細節。 繁瑣細節較少時比較容易看出設計目的。 充分了解這些功能，您將更具生產力、撰寫更具可讀性的程式碼，並且更專注於您的核心功能，而不是語言的建構。

本主題的其餘部分提供這些功能每一個的詳細資料。

## <a name="auto-property-enhancements"></a>Auto 屬性增強功能

自動實作屬性 (通常稱為 Auto 屬性) 的語法讓建立具有簡單 get 和 set 存取子的屬性變得相當容易︰

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

不過，這個簡單的語法限制了您可以使用 Auto 屬性支援的設計類型。 C# 6 改善 Auto 屬性功能，讓您可以在更多案例中使用它們。 您不需要最後求助於更詳細的宣告語法，並且經常以手動方式操作支援欄位。

新的語法可解決唯讀屬性的案例，以及初始化 Auto 屬性背後的變數儲存體。

### <a name="read-only-auto-properties"></a>唯讀 Auto 屬性

「唯讀 Auto 屬性」提供更簡潔的語法，來建立不可變的類型。 在舊版 C# ，您最接近不可變類型的程度是宣告私用 setter：

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
使用這個語法時，編譯器不會確定類型是否確實不可變。 它只會強制使 `FirstName` 和 `LastName` 屬性不會被類別之外的任何程式碼修改。

唯讀 Auto 屬性會啟用真正的唯讀行為。 您只需要用 get 存取子宣告 Auto 屬性︰

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

`FirstName` 和 `LastName` 屬性只能在建構函式主體中設定︰

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

嘗試在另一個方法設定 `LastName` 會產生 `CS0200` 編譯錯誤︰

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

此功能可真正達到建立不可變類型的語言支援，並使用更精簡且方便的 Auto 屬性語法。

如果新增這個語法不會移除可存取的方法，那麼這就是[二進位相容變更](version-update-considerations.md#binary-compatible-changes)。

### <a name="auto-property-initializers"></a>Auto 屬性初始設定式

「Auto 屬性初始設定式」可以讓您宣告 Auto 屬性的初始值作為屬性宣告的一部分。  在舊版中，這些屬性必須有 setter，且您必須使用該 setter 來初始化支援欄位所使用的資料存放區。 請針對學生考慮此類別，其中包含學生的姓名和成績清單︰

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
隨著這個類別成長，您可以包括其他建構函式。 每個建構函式必須初始化這個欄位，否則您將會導致發生錯誤。

C# 6 可讓您在 Auto 屬性宣告中指派 Auto 屬性所使用的儲存體初始值︰

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

`Grades` 成員會在宣告的位置初始化。 這可讓您更輕鬆地只執行初始化一次。 初始化是屬性宣告的一部分，如此能更容易讓儲存區配置與 `Student` 物件的公用介面相等。

屬性初始設定式可以與讀取/寫入屬性一起使用，也可以與唯讀屬性一起使用，如下所示。

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a>具有運算式主體的函式成員

我們撰寫的很多成員主體只包含一個陳述式，它可以表示為運算式。 您可以藉由改為撰寫運算式主體的成員，而減少該語法。 其適用於方法和唯讀屬性。 例如，`ToString()` 覆寫通常是絕佳的候選︰

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

您也可以在唯讀屬性中使用運算式主體的成員︰

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

將現有成員變更為運算式主體成員是[二進位相容變更](version-update-considerations.md#binary-compatible-changes)。


## <a name="using-static"></a>使用靜態

「使用靜態」增強功能可讓您匯入單一類別的靜態方法。 先前，`using` 陳述式會匯入命名空間中的所有類型。 

通常我們會在程式碼中到處使用類別的靜態方法。 重複輸入類別名稱，可能會混淆您的程式碼意義。 常見的範例是當您撰寫類別來執行許多數值計算時。
您的程式碼會散布著 <xref:System.Math.Sin%2A>、<xref:System.Math.Sqrt%2A> 和其他對 <xref:System.Math> 類別中不同方法的呼叫。 新的 `using static` 語法可以讓這些類別容易讀取許多。 您指定正在使用的類別︰

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

現在，您可以使用 <xref:System.Math> 類別中的任何靜態方法，而不需限定 <xref:System.Math> 類別。 <xref:System.Math> 類別是此功能很棒的使用案例，因為它不包含任何執行個體方法。 您也可以使用 `using static` 為同時具有靜態和執行個體方法的類別匯入類別的靜態方法。 其中一個最有用的範例是 <xref:System.String>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> 您必須在靜態 using 陳述式中使用完整的類別名稱 `System.String`。 不能改用 `string` 關鍵字。 

您現在可以呼叫 <xref:System.String> 類別中定義的靜態方法，而不需要將那些方法限定為該類別的成員︰

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

`static using` 功能和擴充方法會以有趣的方式互動，且語言設計包含了明確提供這些互動的一些規則。 目標是在包括您的現有程式碼基底中，將任何可能的重大變更減到最少。

擴充方法只有在使用擴充方法引動語法來呼叫時才會在範圍中，作為靜態方法來呼叫時則否。
您會經常在 LINQ 查詢中看到此情況。 您可以藉由匯入 <xref:System.Linq.Enumerable> 來匯入 LINQ 模式。

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

這樣會匯入 <xref:System.Linq.Enumerable> 類別中的所有方法。
不過，擴充方法只有在呼叫為擴充方法時才會在範圍中。 如果使用靜態方法語法呼叫則不在範圍內︰

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

此決策是因為擴充方法通常使用擴充方法引動運算式來呼叫。 在少數情況下，它們是使用靜態方法呼叫語法來呼叫時，用於解決模稜兩可。
要求在引動過程中使用類別名稱，似乎是明智的做法。

`static using` 有最後一個功能。 `static using` 指示詞也會匯入任何巢狀型別。 那讓您能參照任何巢狀型別而無限定性條件。

## <a name="null-conditional-operators"></a>Null 條件運算子

Null 值會使程式碼變得複雜。 您需要檢查變數的每次存取，以確保您不會為 `null` 取值。 「Null 條件運算子」讓這些檢查更容易且流暢。

只要將成員存取 `.` 取代為 `?.`：

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

在上述範例中，如果 person 物件為 `null`，變數 `first` 便會被指派 `null`。 否則，它會被指派 `FirstName` 屬性的值。 最重要的是，`?.` 表示當 `person` 變數是 `null` 時，這行程式碼不會產生 `NullReferenceException`。 相反地，它會進行最少運算並產生 `null`。

另外，請注意，這個運算式會傳回 `string`，不論 `person` 的值為何。
在最少運算的情況下，傳回的 `null` 值型別會改變以符合完整的運算式。

您可以經常將這個建構與「null 聯合」運算子一起使用，以在其中一個屬性為 `null` 時指派預設值：

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

`?.` 運算子右側的運算元不限於屬性或欄位。
您也可以使用它來條件式地叫用方法。 最常見的成員函數與 Null 條件運算子使用，是安全地叫用可能為 `null` 的委派 (或事件處理常式)。  做法是藉由呼叫委派的 `Invoke` 方法，並使用 `?.` 運算子來存取成員。 如需範例，可參閱  
[委派模式](../delegates-patterns.md#handling-null-delegates)主題。

`?.` 運算子的規則確保運算子的左邊只會評估一次。 這很重要，並且可以啟用許多慣用句，包括使用事件處理常式的範例。 讓我們從事件處理常式用法開始。 在舊版的 C# 中，我們鼓勵您撰寫如下的程式碼︰

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

這比起較簡單的語法而言更為慣用︰

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> 上述範例中介紹競爭條件。 `SomethingHappened` 事件可能在核對 `null` 時有訂閱者，而且這些訂閱者可能在引發事件之前便已被移除。 那會導致擲回 <xref:System.NullReferenceException>。

在第二個版本中，`SomethingHappened` 事件處理常式可能在測試時為非 Null，但如果其他程式碼移除處理常式，它仍可能在呼叫事件處理常式時為 Null。

編譯器會為 `?.` 運算子產生程式碼，確保 `?.` 運算式的左邊 (`this.SomethingHappened`) 只會評估一次，而且結果會加以快取︰

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

確保左邊只評估一次也可讓您對 `?.` 的左邊使用任何運算式，包括方法呼叫。即使有副作用，它們只會評估一次，因此副作用只會發生一次。 您可以在我們的內容看到關於[事件](../events-overview.md#language-support-for-events)的範例。

## <a name="string-interpolation"></a>字串插補

C# 6 包含新的語法，可從字串和可評估的內嵌運算式撰寫字串，以產生其他字串值。

傳統上，您需要在像是 <xref:System.String.Format%2A?displayProperty=nameWithType> 的方法中使用位置參數：

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

使用 C# 6，新的[字串插補](../language-reference/tokens/interpolated.md)功能可讓您將運算式內嵌在字串中。 只要在字串開頭加上 `$`：

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

這個範例將屬性運算式用於替代的運算式。 您可以展開此語法，即能使用任何運算式。 例如，您可能在內插補點的過程中計算某學生的平均成積點︰

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

執行上述範例時，您會發現，`Grades.Average()` 的輸出小數位數可能會超出您想要的位數。 字串內插補點語法支援使用稍早格式化方法時可用的所有格式字串。 您在大括弧內指定了格式字串。 在運算式之後新增 `:` 以格式化︰

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

前一行程式碼會將 `Grades.Average()` 的值格式化為具有兩個小數位數的浮點數。

`:` 一律會解譯為格式化運算式與格式字串之間的分隔符號。 當您的運算式以另一種方式使用 `:` 時 (例如[條件運算子](../language-reference/operators/conditional-operator.md)) 這會導致問題︰

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

在上述範例中，`:` 剖析為格式字串的開頭，而不是條件運算子的一部分。 在發生這種情況的所有情況下，您可以為運算式加上括弧，強制編譯器以您預期的方式解譯運算式︰

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

對於您可以放在大括弧之間的運算式沒有任何限制。 您可以在插入字串內執行複雜的 LINQ 查詢，來執行計算並顯示結果︰

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

您可以從此範例看到，您甚至可以將字串內插補點運算式巢狀放入另一個字串內插補點運算式內。 這個範例很有可能比您想要用在實際執行程式碼的更複雜。
但是，它能夠描述功能的廣度。 任何 C# 運算式都可以放在插入字串的大括號之間。

若要開始使用字串插補，請參閱 [C# 中的字串插補](../tutorials/intro-to-csharp/interpolated-strings.yml)互動式教學課程。

### <a name="string-interpolation-and-specific-cultures"></a>字串內插補點和特定文化特性

在上一節中顯示的所有範例都會使用程式碼執行所在電腦上的目前文化特性來設定字串格式。 通常，您可能需要格式化使用特定文化特性產生的字串。
若要那麼做，請使用物件依可隱含轉換至 <xref:System.FormattableString?displayProperty=nameWithType> 之字串內插補點所產生的事實。

<xref:System.FormattableString> 執行個體包含複合格式字串，以及在將其轉換為字串之前，評估運算式的結果。 使用 <xref:System.FormattableString.ToString(System.IFormatProvider)> 方法以指定設定字串格式時的文化特性。 例如，下列範例會使用德國文化特性產生字串。 (其會使用 ',' 字元作為十進位分隔符號，並使用 '. ' 字元作為千位分隔符號。)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

如需詳細資訊，請參閱[字串插補](../language-reference/tokens/interpolated.md)文章與 [C# 中的字串插補](../tutorials/string-interpolation.md)教學課程。

## <a name="exception-filters"></a>例外狀況篩選條件

C# 6 的另一個新功能是「例外狀況篩選條件」。 例外狀況篩選條件是判斷指定 catch 子句何時應該套用的子句。
如果例外狀況篩選條件所用的運算式評估為 `true`，catch 子句便會對例外狀況執行其一般處理。 如果運算式評估為 `false`，則會略過 `catch` 子句。

用法之一是檢查例外狀況的相關資訊，以判斷 `catch` 子句是否可以處理例外狀況︰

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

例外狀況篩選條件產生的程式碼會提供關於擲回且未處理之例外狀況的更詳細資訊。 在例外狀況篩選條件新增至語言之前，您需要建立程式碼，如下所示︰

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

在這兩個範例之間，例外狀況擲回點會變更。
在先前的程式碼，使用了 `throw` 子句，任何堆疊追蹤分析或損毀傾印的檢查將會顯示已從 catch 子句中的 `throw` 陳述式擲回例外狀況。 實際的例外狀況物件會包含原始呼叫堆疊，但在此擲回點與原始擲回點位置之間的呼叫堆疊中的任何變數所有其他相關資訊都已遺失。 

與使用例外狀況篩選條件之程式碼的處理方式相反︰例外狀況篩選條件運算式會評估為 `false`。 因此，執行永遠不會進入 `catch` 子句。 因為 `catch` 子句不會執行，所以不會發生堆疊回溯的情形。 那表示原始擲回位置會被保留給之後發生的任何偵錯活動。

每當您需要評估例外狀況的欄位或屬性時，請不要只依賴例外狀況類型，而是使用例外狀況篩選條件來保留偵錯的詳細資訊。

例外狀況篩選條件的另一個建議模式是用於記錄的常式。 這種使用方式也會充分利用在例外狀況篩選條件評估為 `false` 時，例外狀況擲回點的保留方式。

記錄方法的引數為無條件地傳回 `false` 的例外狀況：

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

每當您想要記錄例外狀況時，可以新增 catch 子句，並使用這個方法作為例外狀況篩選條件︰

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

例外狀況永遠不會被攔截，因為 `LogException` 方法一律會傳回 `false`。 永遠為 false 的例外狀況篩選條件，表示您可以將此記錄處理常式放在任何其他例外狀況處理常式之前︰

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

上述範例中強調例外狀況篩選條件的一個非常重要的層面。
例外狀況篩選條件讓較一般的例外狀況 catch 子句能夠出現在較特定的例外狀況 catch 子句之前。 此外，也可以讓相同的例外狀況類型出現在多個 catch 子句︰

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

另一種建議的模式有助於避免 catch 子句在附加偵錯工具時，處理例外狀況。 此技術可讓您執行應用程式及偵錯工具，並在擲回例外狀況時停止執行。

在您的程式碼中，新增例外狀況篩選條件，使得只有在未附加偵錯工具時，才會執行任何復原程式碼︰

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

在程式碼中新增此項目之後，您可以設定偵錯工具以在所有未處理的例外狀況處中斷。 在偵錯工具中執行程式，偵錯工具會在 `PerformFailingOperation()` 擲回 `RecoverableException` 時便中斷。
偵錯工具會中斷您的程式，因為 catch 子句不會執行，因為例外狀況篩選條件傳回 false。

## <a name="the-nameof-expression"></a>`nameof` 運算式

`nameof` 運算式評估為符號的名稱。 每當您需要變數、屬性或成員欄位的名稱時，這是讓工具能運作的好方法。

`nameof` 最常見的其中一個用途是提供造成例外狀況的符號名稱︰

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

另一個用途是實作 `INotifyPropertyChanged` 介面的 XAML 應用程式︰

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

使用 `nameof` 運算子相較於常數字串而言的優點，是工具可以了解符號。 如果您使用重整工具來重新命名符號，它會在 `nameof` 運算式中將它重新命名。 常數字串沒有該優點。 您可以在喜好的編輯器中自行嘗試︰重新命名變數，任何 `nameof` 運算式將會一併更新。

`nameof` 運算式會產生其引數的非限定名稱 (上述範例中的 `LastName`)，即使您使用引數的完整格式名稱︰

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

這個 `nameof` 運算式會產生 `FirstName`，而非 `UXComponents.ViewModel.FirstName`。

## <a name="await-in-catch-and-finally-blocks"></a>Catch 和 Finally 區塊中的 Await

C# 5 對於您可以放置 `await` 運算式的位置有數個限制。
其中一個在 C# 6 中已移除。 您現在可以在 `catch` 或 `finally` 運算式中使用 `await`。 

在 catch 和 finally 區塊中新增 await 運算式可能會讓這些的處理方式變複雜。 讓我們新增一個範例討論這會如何。 在任何非同步方法中，您可以在 finally 子句使用 await 運算式。

使用 C# 6，您也可以在 catch 運算式中使用 await。 這最常用於記錄情節︰

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

在 `catch` 和 `finally` 子句內新增 `await` 支援的實作詳細資料，可確保行為與同步程式碼的行為一致。 當 `catch` 或 `finally` 子句中執行的程式碼擲回時，執行會在下個周圍區塊中尋找適合的 `catch` 子句。 如果有目前的例外狀況，該例外狀況將會遺失。 `catch` 和 `finally` 子 句中等候的運算式也會發生相同的情況︰搜尋適合的 `catch`，目前的例外狀況 (如果有的話) 將會遺失。  

> [!NOTE]
> 此行為是建議您小心撰寫 `catch` 和 `finally` 子句的原因，以避免產生新的例外狀況。

## <a name="index-initializers"></a>索引初始設定式

「索引初始設定式」是讓集合初始設定式與索引使用方式更一致的兩個功能之一。 在舊版的 C# 中，您可以只搭配序列樣式集合來使用「集合初始設定式」，包括在索引鍵值/組前後加上大括號的 <xref:System.Collections.Generic.Dictionary%602>：

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

現在，您可以使用它們來搭配 <xref:System.Collections.Generic.Dictionary%602> 集合與類似的型別。 新的語法支援使用集合中的索引進行指派：

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

此功能表示可以使用類似於已可供數個版本的序列容器使用的語法，將關聯容器初始化。

## <a name="extension-add-methods-in-collection-initializers"></a>集合初始設定式中的擴充 `Add` 方法

能夠輕鬆進行集合初始設定的另一個功能，是可以針對 `Add` 方法使用「擴充方法」。 新增此功能是為了與 Visual Basic 相當。 

當您的自訂集合類別具有不同名稱的方法，可以在語意上新增項目時，此功能最實用。

例如，請考慮如下的學生集合︰

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

`Enroll` 方法會新增學生。 但它不是採用 `Add` 模式。
在舊版的 C# 中，您無法使用集合初始設定式搭配 `Enrollment` 物件︰

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

現在您可以，但是只有當您建立將 `Add` 對應至 `Enroll` 的擴充方法時：

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

您使用此功能做的事，是藉由建立擴充方法，將任何新增項目到集合的方法對應至名為 `Add` 的方法。

## <a name="improved-overload-resolution"></a>改進的多載解析

您可能不會發現最後這個功能。 在有些建構中，舊版 C# 編譯器可能會發現一些涉及 Lambda 運算式的方法呼叫為模稜兩可。 請參考下列方法：

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

在舊版的 C# 中，使用方法群組語法呼叫該方法會失敗︰

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
舊版的編譯器無法正確分辨 `Task.Run(Action)` 和 `Task.Run(Func<Task>())`。 在舊版中，您必須使用 Lambda 運算式作為引數︰

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

C# 6 編譯器可正確判斷 `Task.Run(Func<Task>())` 是較好的選擇。

### <a name="deterministic-compiler-output"></a>deterministic 編譯器選項

`-deterministic` 選項會指示編譯器針對相同原始程式檔 的後續編譯產生位元組對位元組的相同輸出組件。

根據預設，每次編譯會針對每次編譯產生唯一的輸出。 編譯器會新增時間戳記，以及從亂數產生的 GUID。 如果您想要比較位元組對位元組的輸出，以確保組建的一致性，您可以使用此選項。

如需詳細資訊，請參閱 [-deterministic 編譯器選項](../language-reference/compiler-options/deterministic-compiler-option.md)文章。

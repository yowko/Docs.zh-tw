---
title: C# 6 的新功能 - C# 指南
description: 了解 C# 第 6 版的新功能
ms.date: 12/12/2018
ms.openlocfilehash: 49247109bd1acbf697f5700b5cfe9a2b85393b2c
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235715"
---
# <a name="whats-new-in-c-6"></a>C# 6 的新功能

C# 6.0 版包含許多功能，能提升開發人員的產能。 這些功能的整體影響是您可撰寫更簡潔且更具可讀性的程式碼，。 語法包含許多常見做法的較少繁瑣細節。 繁瑣細節較少時比較容易看出設計目的。 徹底了解這些功能，可讓您提升生產力，並撰寫更容易閱讀的程式碼。 您可以更專注於您的功能，而不是語言的建構。

此文章的其餘部分將概述每項功能，並提供連結以探索每項功能。 您也可以在＜教學課程＞一節的 [C# 6 互動式探索](../tutorials/exploration/csharp-6.yml)中探索這些功能。

## <a name="read-only-auto-properties"></a>唯讀 Auto 屬性

「唯讀 Auto 屬性」  提供更簡潔的語法，來建立不可變的類型。 您只需要用 get 存取子宣告 Auto 屬性︰

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

這項功能可真正達到建立不可變類型的語言支援，並使用更精簡且方便的 Auto 屬性語法。

如果新增這個語法不會移除可存取的方法，那麼這就是[二進位相容變更](version-update-considerations.md#binary-compatible-changes)。

## <a name="auto-property-initializers"></a>Auto 屬性初始設定式

「Auto 屬性初始設定式」  可以讓您宣告 Auto 屬性的初始值作為屬性宣告的一部分。

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

`Grades` 成員會在宣告的位置初始化。 這可讓您更輕鬆地只執行初始化一次。 初始化是屬性宣告的一部分，如此能更容易讓儲存區配置與 `Student` 物件的公用介面相等。

## <a name="expression-bodied-function-members"></a>具有運算式主體的函式成員

您撰寫的許多成員都是單一陳述式，而這些陳述式可能是單一運算式。 請改為撰寫運算式主體成員。 其適用於方法和唯讀屬性。 例如，`ToString()` 覆寫通常是絕佳的候選︰

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

您也可以將此語法用於唯讀屬性：

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

將現有成員變更為運算式主體成員是[二進位相容變更](version-update-considerations.md#binary-compatible-changes)。

## <a name="using-static"></a>使用靜態

「使用靜態」  增強功能可讓您匯入單一類別的靜態方法。 您指定正在使用的類別︰

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<xref:System.Math> 不包含任何執行個體方法。 您也可以使用 `using static` 為同時具有靜態和執行個體方法的類別匯入類別的靜態方法。 其中一個最有用的範例是 <xref:System.String>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> 您必須在靜態 using 陳述式中使用完整的類別名稱 `System.String`。  不能改用 `string` 關鍵字。

如果從 `static using` 陳述式匯入，擴充方法只有在使用擴充方法引動過程語法來呼叫時才會在範圍中。 它們在作為靜態方法呼叫時，則不在範圍中。 您會經常在 LINQ 查詢中看到此情況。 您可以藉由匯入 <xref:System.Linq.Enumerable> 或 <xref:System.Linq.Queryable> 來匯入 LINQ 模式。

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

您通常會使用擴充方法引動過程運算式來呼叫擴充方法。 在您使用靜態方法呼叫語法來呼叫它們的少數情況下，新增類別名稱可解決語意模糊問題。

`static using` 指示詞也會匯入任何巢狀型別。 您可以參照任何巢狀型別而無限定性條件。

## <a name="null-conditional-operators"></a>Null 條件運算子

「Null 條件運算子」  讓 Null 檢查更容易且流暢。 請將成員存取 `.` 取代為 `?.`：

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

在上述範例中，如果 person 物件為 `null`，變數 `first` 便會被指派 `null`。 否則，會為其指派 `FirstName` 屬性的值。 最重要的是，`?.` 表示當 `person` 變數是 `null` 時，這行程式碼不會產生 `NullReferenceException`。 相反地，它會進行最少運算並傳回 `null`。 您也可以使用 Null 條件運算子來進行陣列或索引子存取。 請在索引運算式中將 `[]` 取代為 `?[]`。

不論 `person` 的值為何，下列運算式都會傳回 `string`。 您經常將這個建構與「Null 聯合」  運算子一起使用，以便在其中一個屬性為 `null` 時指派預設值。 當運算式進行最少運算時，傳回的 `null` 值型別會改變以符合完整的運算式。

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

您也可以使用 `?.` 來進行方法的條件式叫用。 成員函式搭配 Null 條件運算子的最常見用法，是安全地叫用可能為 `null` 的委派 (或事件處理常式)。  您將使用 `?.` 運算子呼叫委派的 `Invoke` 方法來存取成員。 如需範例，請參閱[委派模式](../delegates-patterns.md#handling-null-delegates)一文。

`?.` 運算子的規則確保運算子的左邊只會評估一次。 它可啟用許多慣用句，包括使用事件處理常式的下列範例：

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

確保左側只評估一次也可讓您在 `?.` 的左側使用任何運算式，包括方法呼叫

## <a name="string-interpolation"></a>字串插補

使用 C# 6，新的[字串插補](../language-reference/tokens/interpolated.md)功能可讓您將運算式內嵌在字串中。 只需要在字串前面加上 `$`，並在 `{` 與 `}` 之間使用運算式而不是序數：

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

這個範例將屬性用於替代的運算式。 您可以使用任何運算式。 比方說，您可能在內插補點的過程中計算某學生的平均成積點︰

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

前一行程式碼會將 `Grades.Average()` 的值格式化為具有兩個小數位數的浮點數。

通常，您可能需要格式化使用特定文化特性產生的字串。 您會利用字串插補所產生的物件可隱含轉換為 <xref:System.FormattableString?displayProperty=nameWithType> 的事實。 <xref:System.FormattableString> 執行個體包含複合格式字串，以及在將其轉換為字串之前，評估運算式的結果。 使用 <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> 方法以指定設定字串格式時的文化特性。 下列範例會使用德國 (de-DE) 文化特性產生字串。 (根據預設，德國文化特性會使用 ',' 字元作為十進位分隔符號，並使用 '. ' 字元作為千位分隔符號。)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

若要開始使用字串插補，請參閱 [C# 中的字串插補](../tutorials/exploration/interpolated-strings.yml)互動式教學課程、[字串插補](../language-reference/tokens/interpolated.md)一文，以及 [C# 中的字串插補](../tutorials/string-interpolation.md)教學課程。

## <a name="exception-filters"></a>例外狀況篩選條件

*例外狀況篩選條件*是判斷指定 catch 子句何時應該套用的子句。 如果例外狀況篩選條件所用的運算式評估為 `true`，catch 子句便會對例外狀況執行其一般處理。 如果運算式評估為 `false`，則會略過 `catch` 子句。 用法之一是檢查例外狀況的相關資訊，以判斷 `catch` 子句是否可以處理例外狀況︰

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a>`nameof` 運算式

[nameof](../language-reference/operators/nameof.md) 運算式評估為符號的名稱。 每當您需要變數、屬性或成員欄位的名稱時，這是讓工具能運作的好方法。 `nameof` 最常見的其中一個用途是提供造成例外狀況的符號名稱︰

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

另一個用途是實作 `INotifyPropertyChanged` 介面的 XAML 型應用程式：

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a>Catch 和 Finally 區塊中的 Await

C# 5 對於您可以放置 `await` 運算式的位置有數個限制。 透過 C# 6，您現在可以在 `catch` 或 `finally` 運算式中使用 `await`。 這最常用於記錄情節︰

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

在 `catch` 和 `finally` 子句內新增 `await` 支援的實作詳細資料，可確保行為與同步程式碼的行為一致。 當 `catch` 或 `finally` 子句中執行的程式碼擲回時，執行會在下個周圍區塊中尋找適合的 `catch` 子句。 如果有目前的例外狀況，該例外狀況將會遺失。 `catch` 和 `finally` 子 句中等候的運算式也會發生相同的情況︰搜尋適合的 `catch`，目前的例外狀況 (如果有的話) 將會遺失。  

> [!NOTE]
> 此行為是建議您小心撰寫 `catch` 和 `finally` 子句的原因，以避免產生新的例外狀況。

## <a name="initialize-associative-collections-using-indexers"></a>使用索引子初始化關聯集合

「索引初始設定式」  是讓集合初始設定式與索引使用方式更一致的兩個功能之一。 在舊版的 C# 中，您可以在索引鍵值/組前後新增大括弧，藉以搭配序列樣式集合 (包括 <xref:System.Collections.Generic.Dictionary%602>) 來使用「集合初始設定式」  ：

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

您可將它們與 <xref:System.Collections.Generic.Dictionary%602> 集合和其他類型一起使用，其中可存取的 `Add` 方法接受一個以上的引數。 新的語法支援使用集合中的索引進行指派：

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

這項功能表示可以使用類似於已可供數個版本的序列容器使用的語法，將關聯容器初始化。

## <a name="extension-add-methods-in-collection-initializers"></a>集合初始設定式中的擴充 `Add` 方法

能夠輕鬆進行集合初始設定的另一個功能，是可以針對 `Add` 方法使用「擴充方法」  。 新增這項功能是為了與 Visual Basic 相當。 當您的自訂集合類別具有不同名稱的方法，可以在語意上新增項目時，此功能最實用。

## <a name="improved-overload-resolution"></a>改進的多載解析

您可能不會發現最後這項功能。 在有些建構中，舊版 C# 編譯器可能會發現一些涉及 Lambda 運算式的方法呼叫為模稜兩可。 請參考下列方法：

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

在舊版的 C# 中，使用方法群組語法呼叫該方法會失敗︰

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

舊版的編譯器無法正確分辨 `Task.Run(Action)` 與 `Task.Run(Func<Task>())`。 在舊版中，您必須使用 Lambda 運算式作為引數︰

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

C# 6 編譯器可正確判斷 `Task.Run(Func<Task>())` 是較好的選擇。

### <a name="deterministic-compiler-output"></a>deterministic 編譯器選項

`-deterministic` 選項會指示編譯器針對相同原始程式檔 的後續編譯產生位元組對位元組的相同輸出組件。

根據預設，每次編譯會針對每次編譯產生唯一的輸出。 編譯器會新增時間戳記，以及從亂數產生的 GUID。 如果您想要比較位元組對位元組的輸出，以確保組建的一致性，您可以使用此選項。

如需詳細資訊，請參閱 [-deterministic 編譯器選項](../language-reference/compiler-options/deterministic-compiler-option.md)文章。

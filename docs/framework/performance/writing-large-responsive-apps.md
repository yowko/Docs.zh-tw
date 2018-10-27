---
title: 撰寫大型、可回應的 .NET Framework 應用程式
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 947e443fc1561e86cf9c5fe7c19d4290cc364bd5
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50170376"
---
# <a name="writing-large-responsive-net-framework-apps"></a>撰寫大型、可回應的 .NET Framework 應用程式
本文針對大型 .NET Framework 應用程式或處理大量資料 (例如檔案或資料庫) 的應用程式，提供可提升其效能的提示。 這些提示來自於以 Managed 程式碼重寫 C# 和 Visual Basic 編譯器，本文包含數個 C# 編譯器的實際範例。  
  
 使用 .NET Framework 建置應用程式的效率很高。  這些強大且安全的語言和豐富的程式庫集合，可大幅提升應用程式的建置效能。  然而，生產力愈高，代表所負的責任愈大。  您應該充分利用 .NET Framework 的所有功能，但視需要隨時調整程式碼的效能。  
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a>新編譯器效能適用於您的應用程式的原因  
 .NET 編譯器平台 ("Roslyn") 小組以 Managed 程式碼重寫 C# 和 Visual Basic 編譯器，提供新的應用程式開發介面，以便模型化和分析程式碼、建置工具，以及提供更豐富並感知程式碼的 Visual Studio 體驗。  重寫編譯器並在新編譯器上建置 Visual Studio 體驗，顯示了實用的效能深入資訊，適用於任何大型 .NET Framework 應用程式或任何處理大量資料的應用程式。  您不需要了解編譯器，也能利用 C# 編譯器的深入資訊和範例。  
  
 Visual Studio 使用編譯器應用程式開發介面建置使用者偏好的所有 IntelliSense 功能，例如以顏色標示識別項和關鍵字、語法完成清單、錯誤波浪線、參數提示、程式碼問題和程式碼動作。  Visual Studio 會在開發人員輸入及變更其程式碼時提供此說明，並且 Visual Studio 必須在編譯器持續模型化開發人員編輯的程式碼時保持回應。  
  
 當您的使用者與您的應用程式互動時，他們期望應用程式會有回應。  因此，請不要封鎖輸入或命令處理等動作。  說明應該迅速快顯，或在使用者繼續輸入時放棄顯示。  您的應用程式應該避免冗長的運算使得應用程式緩慢，而導致封鎖 UI 執行緒。  
  
 如需 Roslyn 編譯器的詳細資訊，請參閱[.NET 編譯器平台 SDK](../../csharp/roslyn-sdk/index.md)。
  
## <a name="just-the-facts"></a>認清事實  
 調整效能和建立回應能力佳的 .NET Framework 應用程式時，請考慮下列幾點事實。  
  
### <a name="fact-1-dont-prematurely-optimize"></a>事實 1：不要太早進行最佳化  
 撰寫比所需還要複雜的程式碼，會產生維護、偵錯和修改成本。  有經驗的程式設計人員直覺便知道如何解決程式碼問題，以及如何撰寫更有效率的程式碼。  不過，他們有時會太早最佳化程式碼。  例如，他們可能會在簡單陣列便已足夠的情況下，使用雜湊資料表；或者使用可能會造成記憶體流失的複雜快取，而不直接重新計算值。  即使您是有經驗的程式設計人員，仍應測試效能，並在發現問題時分析程式碼。  
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a>事實 2：未經測量，不過是臆測  
 程式碼剖析和測量資料不會說謊。  程式碼剖析顯示 CPU 是否滿載，或者磁碟 I/O 是否發生封鎖的情況。  程式碼剖析告訴您目前配置的記憶體類型和數量，以及您的 CPU 是否花很多時間在[記憶體回收](../../../docs/standard/garbage-collection/index.md) (GC)。  
  
 您應該為應用程式中的關鍵客戶體驗或案例設定效能目標，並撰寫測試以測量效能。  應用科學方法來調查失敗的測試：使用程式碼剖析來引導您、假設可能的問題，以及透過實驗或變更程式碼來測試您的假設。  透過定期測試建立一段時間的基準效能測量資料，以便您隔離出導致效能降低的變更。  當您以嚴謹的方式來處理效能工作時，便可避免浪費時間在不必要的程式碼更新。  
  
### <a name="fact-3-good-tools-make-all-the-difference"></a>事實 3：使用良好工具的成果大不相同  
 良好工具可讓您快速鑽研最大的效能問題 (CPU、記憶體或磁碟)，並協助您找出導致這些瓶頸的程式碼。  Microsoft 提供各種效能工具，例如 [Visual Studio 程式碼剖析工具](/visualstudio/profiling/beginners-guide-to-performance-profiling)、[Windows Phone 分析工具](https://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f)和 [PerfView](https://www.microsoft.com/download/details.aspx?id=28567)。  
  
 PerfView 是非常強大的免費工具，可協助您專注於深入的問題，例如磁碟 I/O、GC 事件和記憶體。  您可以擷取與效能相關的 [Windows 事件追蹤](../../../docs/framework/wcf/samples/etw-tracing.md) (ETW) 事件，並輕鬆檢視每種應用程式、處理序、堆疊和執行緒的資訊。  PerfView 顯示您的應用程式配置的記憶體數量和類型，以及哪些函式或呼叫堆疊佔用了多少記憶體配置。 如需詳細資訊，請參閱工具隨附的豐富說明主題、示範和影片 (例如 Channel 9 上的 [PerfView Tutorial](https://channel9.msdn.com/Series/PerfView-Tutorial) (PerfView 教學課程)。  
  
### <a name="fact-4-its-all-about-allocations"></a>事實 4：重點在於配置  
 您可能會認為建置回應能力佳的 .NET Framework 應用程式的重點在於演算法，例如使用快速排序取代反昇排序，但實際上卻不然。  配置記憶體才是建置回應能力佳的應用程式的最大要素，特別是當您的應用程式很龐大或處理大量資料時。  
  
 使用新編譯器應用程式開發介面建置回應能力佳的 IDE 體驗的幾乎所有工作，都與避免配置和管理快取策略相關。  PerfView 追蹤顯示新的 C# 和 Visual Basic 編譯器的效能很少佔用龐大的 CPU 資源。  當編譯器讀取數十萬或數百萬行程式碼、讀取中繼資料或發出產生的程式碼時，可能會受限於 I/O。  UI 執行緒延遲幾乎全部都是由於記憶體回收所造成。  .NET Framework GC 為了效能而高度調整，並在應用程式的程式碼執行同時執行大部分的工作。  但是，單一配置可能會觸發耗費大量資源的[gen2](../../../docs/standard/garbage-collection/fundamentals.md) 收集，並停止所有執行緒。  
  
## <a name="common-allocations-and-examples"></a>常見配置和範例  
 本節中的範例運算式隱藏了看起來很小的配置。  但是，如果大型應用程式執行運算式夠多次，則可能造成數百個 MB，甚至是 GB 的配置。  例如，模擬開發人員在編輯器中輸入的一分鐘測試，會配置數 GB 記憶體，而導致效能小組專注於輸入案例。  
  
### <a name="boxing"></a>Boxing  
 當通常存留在堆疊或資料結構中的實值型別包裝在物件中時，會發生 [Boxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md)。  換句話說，您可以配置保存資料的物件，再傳回物件的指標。  .NET Framework 有時由於方法的簽章或儲存位置的類型而以 Boxing 處理值。  在物件中包裝實值類型會導致記憶體配置。  許多 Boxing 作業可能導致數 MB 或 GB 的應用程式配置，這表示您的應用程式會造成更多 GC。 .NET Framework 和語言編譯器會盡可能避免 Boxing，但有時還是會在您預想不到的情況下發生。  
  
 若要在 PerfView 中查看 Boxing，請開啟追蹤，然後檢視您的應用程式之處理序名稱下的 GC Heap Alloc Stacks (請記住，PerfView 會報告所有處理序)。  如果您在配置下看到類似 <xref:System.Int32?displayProperty=nameWithType> 和 <xref:System.Char?displayProperty=nameWithType> 的類型，則表示您以 Boxing 處理實值類型。  選擇其中一種類型可顯示以 Boxing 處理類型所在的堆疊和函式。  
  
 **範例 1：字串方法和實值型別引數**  
  
 此範例程式碼描述可能不必要和多餘的 Boxing：  
  
```csharp  
public class Logger  
{  
    public static void WriteLine(string s) { /*...*/ }  
}  
  
public class BoxingExample  
{  
    public void Log(int id, int size)  
    {  
        var s = string.Format("{0}:{1}", id, size);  
        Logger.WriteLine(s);  
    }  
}  
```  
  
 此程式碼提供記錄功能，因此應用程式可經常呼叫 `Log` 函式，可能呼叫數百萬次。  問題是 `string.Format` 的呼叫會解析成 <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> 多載。  
  
 此多載需要 .NET Framework 將 `int` 值 Boxing 為物件，以傳遞至此方法呼叫。  呼叫 `id.ToString()` 和 `size.ToString()`，並將所有字串 (即物件) 傳遞至 `string.Format` 呼叫，可修正一部分問題。  呼叫 `ToString()` 不會配置字串，但是 `string.Format` 內仍然會發生配置。  
  
 您可能會認為對 `string.Format` 的這個基本呼叫只是字串串連，而將此程式碼改寫如下：  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 但是，該行程式碼由於符合 <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>，因此會引進 Boxing 配置。  .NET Framework 必須以 Boxing 處理叫用 `Concat` 的字元常值。  
  
 **範例 1 的修正**  
  
 完整修正很簡單。  只要以字串常值取代字元常值即可，由於字串已經是物件，因此不會發生任何 Boxing：  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 **範例 2：列舉 Boxing**  
  
 此範例由於經常使用列舉類型 (特別是在字典查閱作業中)，因此會在新的 C# 和 Visual Basic 編譯器中造成大量配置。  
  
```csharp  
public enum Color  
{  
    Red, Green, Blue  
}  
  
public class BoxingExample  
{  
    private string name;  
    private Color color;  
    public override int GetHashCode()  
    {  
        return name.GetHashCode() ^ color.GetHashCode();  
    }  
}  
```  
  
 這個問題很棘手。  基於實作原因，此方法會以 Boxing 處理列舉類型的基本表示，因此 PerfView 會將此報告為 <xref:System.Enum.GetHashCode> Boxing。  如果您在 PerfView 中進一步檢視，您會看到 <xref:System.Enum.GetHashCode> 的每個呼叫有兩個 Boxing 配置。   編譯器會插入其中一個配置，而 .NET Framework 會插入另一個配置。  
  
 **範例 2 的修正**  
  
 您可以在呼叫 <xref:System.Enum.GetHashCode> 之前轉換為基本表示，輕鬆避免這兩個配置。  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 以 Boxing 處理列舉類型的另一個常見來源是 <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> 方法。  傳遞至 <xref:System.Enum.HasFlag%28System.Enum%29> 的引數必須為 Boxed。  在大多數情況下，比較簡單且不需要配置的作法是以位元測試取代 <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> 的呼叫。  
  
 請記住第一點效能事實 (即不要太早進行最佳化)，不要以此方式開始重寫所有程式碼。    留意這些 Boxing 成本，但只在對應用程式進行程式碼分析並找出作用點之後變更程式碼。  
  
### <a name="strings"></a>字串  
 字串操作是造成配置問題的一些最主要原因，通常會在 PerfView 中顯示為前五大配置。  程式在序列化、JSON 和 REST 應用程式開發介面中都會用到字串。  當您無法使用列舉類型時，您可以使用字串做為與系統互通的程式設計常數。  當您的程式碼分析顯示字串高度影響效能時，請尋找 <xref:System.String> 方法的呼叫，例如 <xref:System.String.Format%2A>、<xref:System.String.Concat%2A>、<xref:System.String.Split%2A>、<xref:System.String.Join%2A>、<xref:System.String.Substring%2A> 等。  使用 <xref:System.Text.StringBuilder> 可避免需要從許多說明建立一個字串的成本，但即使是配置 <xref:System.Text.StringBuilder> 物件也可能成為需要管理的瓶頸。  
  
 **範例 3：字串作業**  
  
 C# 編譯器包含下列程式碼，用以撰寫格式化之 XML 文件註解的文字：  
  
```csharp  
public void WriteFormattedDocComment(string text)  
{  
    string[] lines = text.Split(new[] { "\r\n", "\r", "\n" },  
                                StringSplitOptions.None);  
    int numLines = lines.Length;  
    bool skipSpace = true;  
    if (lines[0].TrimStart().StartsWith("///"))  
    {  
        for (int i = 0; i < numLines; i++)  
        {  
            string trimmed = lines[i].TrimStart();  
            if (trimmed.Length < 4 || !char.IsWhiteSpace(trimmed[3]))  
            {  
                skipSpace = false;  
                break;  
            }  
        }  
        int substringStart = skipSpace ? 4 : 3;  
        for (int i = 0; i < numLines; i++)  
            WriteLine(lines[i].TrimStart().Substring(substringStart));  
    }  
    else { /* ... */ }  
```  
  
 您會看到此程式碼執行許多字串操作。  此程式碼使用程式庫方法將多行程式碼分割成不同的字串、修剪空格、檢查引數 `text` 是否為 XML 文件註解，以及從多行程式碼擷取子字串。  
  
 在 `WriteFormattedDocComment` 內的第一行，`text.Split` 呼叫會在每次呼叫時，配置新的三元素陣列做為引數。  編譯器每次都必須發出程式碼，才能配置此陣列。  這是因為編譯器不確定 <xref:System.String.Split%2A> 是否將陣列儲存在其他位置，而其他程式碼可能修改了該位置的陣列，而影響對 `WriteFormattedDocComment` 的稍後呼叫。  呼叫 <xref:System.String.Split%2A> 也會為 `text` 中的每一行配置一個字串，並配置其他記憶體以執行操作。  
  
 `WriteFormattedDocComment` 對 <xref:System.String.TrimStart%2A> 方法有三個呼叫。  其中兩個呼叫在內部迴圈中，會複製工作和配置。  更糟的是，除了產生字串，呼叫不含引數的 <xref:System.String.TrimStart%2A> 方法還會配置空陣列 (針對 `params` 參數)。  
  
 最後是 <xref:System.String.Substring%2A> 方法的呼叫，此呼叫通常會配置新字串。  
  
 **範例 3 的修正**  
  
 與先前的範例不同，稍微修改並無法修正這些配置。  您必須退一步檢視問題，以不同的方式來解決問題。  例如，您會注意到 `WriteFormattedDocComment()` 的引數是含有方法需要之所有資訊的字串，因此程式碼會執行更多索引作業，而不是配置許多部分字串。  
  
 編譯器的效能小組可透過類似如下的程式碼來處理所有配置：  
  
```csharp  
private int IndexOfFirstNonWhiteSpaceChar(string text, int start) {  
    while (start < text.Length && char.IsWhiteSpace(text[start])) start++;  
    return start;  
}  
  
private bool TrimmedStringStartsWith(string text, int start, string prefix) {  
    start = IndexOfFirstNonWhiteSpaceChar(text, start);  
    int len = text.Length - start;  
    if (len < prefix.Length) return false;  
    for (int i = 0; i < len; i++)  
    {  
        if (prefix[i] != text[start + i]) return false;  
    }  
    return true;  
}  
  
// etc...  
```  
  
 `WriteFormattedDocComment()` 的第一個版本已配置一個陣列、數個子字串、經修剪的子字串，以及空的 `params` 陣列。  它也會檢查 `"///"`。  修訂過的程式碼只會使用索引，而不會進行任何配置。  它會找出非空格的第一個字元，並接著逐字元檢查以查看字串的開頭是否為 `"///"`。  新的程式碼會使用`IndexOfFirstNonWhiteSpaceChar`而不是<xref:System.String.TrimStart%2A>後，傳回第一個索引 （指定的起始索引） 發生非空格字元。  此修正並不完整，不過您可以查看如何套用類似的修正以取得完整的解決方法。  您可以在整個程式碼中應用此方法，來移除 `WriteFormattedDocComment()` 中的所有配置。  
  
 **範例 4：StringBuilder**  
  
 此範例使用 <xref:System.Text.StringBuilder> 物件。  下列函式會為泛型類型產生完整的類型名稱：  
  
```csharp  
public class Example  
{  
    // Constructs a name like "SomeType<T1, T2, T3>"  
    public string GenerateFullTypeName(string name, int arity)  
    {  
        StringBuilder sb = new StringBuilder();  
  
        sb.Append(name);  
        if (arity != 0)  
        {  
            sb.Append("<");  
            for (int i = 1; i < arity; i++)  
            {  
                sb.Append("T"); sb.Append(i.ToString()); sb.Append(", ");  
            }  
            sb.Append("T"); sb.Append(i.ToString()); sb.Append(">");  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
 重點在於建立新的 <xref:System.Text.StringBuilder> 執行個體的程式行。  此程式碼造成 `sb.ToString()` 的配置和 <xref:System.Text.StringBuilder> 實作中的內部配置，但是如果您需要字串結果，則無法控制這些配置。  
  
 **範例 4 的修正**  
  
 若要修正 `StringBuilder` 物件配置，請快取此物件。  即使快取可能拋棄的單一執行個體，仍會大幅提升效能。  這是此函式的新實作，會省略新的第一行和最後一行以外的所有程式碼：  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 主要部分是新的 `AcquireBuilder()` 和 `GetStringAndReleaseBuilder()` 函式：  
  
```csharp  
[ThreadStatic]  
private static StringBuilder cachedStringBuilder;  
  
private static StringBuilder AcquireBuilder()  
{  
    StringBuilder result = cachedStringBuilder;  
    if (result == null)  
    {  
        return new StringBuilder();  
    }  
    result.Clear();  
    cachedStringBuilder = null;  
    return result;  
}  
  
private static string GetStringAndReleaseBuilder(StringBuilder sb)  
{  
    string result = sb.ToString();  
    cachedStringBuilder = sb;  
    return result;  
}  
```  
  
 由於新編譯器使用執行緒，因此這些實作使用執行緒靜態欄位 (<xref:System.ThreadStaticAttribute> 屬性) 來快取 <xref:System.Text.StringBuilder>，並且您有可能會放棄 `ThreadStatic` 宣告。  執行緒靜態欄位保存執行此程式碼之每個執行緒的唯一值。  
  
 清除並將欄位或快取設定為 null 之後，`AcquireBuilder()` 會傳回快取的 <xref:System.Text.StringBuilder> 執行個體 (如果有的話)。  否則，`AcquireBuilder()` 會建立並傳回新執行個體，並將欄位或快取保持設定為 null。  
  
 當您完成 <xref:System.Text.StringBuilder> 時，您可以呼叫 `GetStringAndReleaseBuilder()` 以取得字串結果、儲存欄位或快取中的 <xref:System.Text.StringBuilder> 執行個體，然後傳回結果。  執行作業可能會重新輸入此程式碼，並建立多個 <xref:System.Text.StringBuilder> 物件 (不過這不常發生)。  此程式碼只會儲存最後發行的 <xref:System.Text.StringBuilder> 執行個體，以供稍後使用。  此簡單的快取策略會大幅降低新編譯器中的配置。  .NET Framework 和 MSBuild ("MSBuild") 的組件使用類似的技術來提升效能。  
  
 此簡單的快取策略遵守良好的快取設計，因為該策略具有大小限制。  但是，現在的程式碼比原始程式碼更多，這表示維護成本會更高。  您應該僅在發現效能問題時才採用快取策略，而 PerfView 顯示 <xref:System.Text.StringBuilder> 配置是影響效能的主要因素。  
  
### <a name="linq-and-lambdas"></a>LINQ 和 Lambdas  
Language Integrated Query (LINQ)，搭配使用 lambda 運算式是產能功能的範例。 不過，它的使用可能會對經過一段時間，效能的重大的影響，而且您可能會發現您需要重寫程式碼。
  
 **範例 5：Lambdas、List\<T> 和 IEnumerable\<T>**  
  
 這個範例會使用 [LINQ 和功能樣式程式碼](https://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx)來找出編譯器模型中的符號，並指定名稱字串：  
  
```csharp  
class Symbol {  
    public string Name { get; private set; }  
    /*...*/  
}  
  
class Compiler {  
    private List<Symbol> symbols;  
    public Symbol FindMatchingSymbol(string name)  
    {  
        return symbols.FirstOrDefault(s => s.Name == name);  
    }  
}  
```  
  
 新編譯器和建置在其上的 IDE 體驗會很頻繁地呼叫 `FindMatchingSymbol()`，並且此函式的一行程式碼中有多個隱藏的配置。  若要檢查這些配置，請先將此函式的一行程式碼分成兩行：  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 在第一行中， [lambda 運算式](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [覆蓋](https://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx)區域變數`name`。  這表示除了配置 `predicate` 保存的[委派](~/docs/csharp/language-reference/keywords/delegate.md)物件之外，此程式碼還會配置靜態類別，以維持可擷取 `name` 值的環境。  此編譯器產生類似如下的程式碼：  
  
```csharp  
// Compiler-generated class to hold environment state for lambda  
private class Lambda1Environment  
{  
    public string capturedName;  
    public bool Evaluate(Symbol s)  
    {  
        return s.Name == this.capturedName;  
    }  
}  
  
// Expanded Func<Symbol, bool> predicate = s => s.Name == name;  
Lambda1Environment l = new Lambda1Environment() { capturedName = name };  
var predicate = new Func<Symbol, bool>(l.Evaluate);  
```  
  
 這兩個 `new` 配置 (一個用於環境類別，一個用於委派) 現在是明確的。  
  
 接著檢視 `FirstOrDefault` 的呼叫。 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 類型上的這個擴充方法也會造成配置。  由於 `FirstOrDefault` 將 <xref:System.Collections.Generic.IEnumerable%601> 物件當做它的第一個引數，因此您可以將呼叫擴充成下列程式碼 (稍微簡化以便討論)：  
  
```csharp  
// Expanded return symbols.FirstOrDefault(predicate) ...  
     IEnumerable<Symbol> enumerable = symbols;  
     IEnumerator<Symbol> enumerator = enumerable.GetEnumerator();  
     while(enumerator.MoveNext())  
     {  
         if (predicate(enumerator.Current))  
             return enumerator.Current;  
     }  
     return default(Symbol);  
```  
  
 `symbols` 變數具有 <xref:System.Collections.Generic.List%601> 類型。  <xref:System.Collections.Generic.List%601> 集合類型實作 <xref:System.Collections.Generic.IEnumerable%601>，並巧妙地定義 <xref:System.Collections.Generic.IEnumerator%601> 透過 <xref:System.Collections.Generic.List%601> 實作的列舉值 (`struct` 介面)。  使用結構取代類別表示您通常會避免任何堆積配置，並進而影響記憶體回收效能。  列舉值通常可以搭配語言的 `foreach` 迴圈使用，該迴圈使用列舉值傳回時在呼叫堆疊上的列舉值結構。  累加呼叫堆疊指標以挪出空間給物件，不會對 GC 造成堆積配置所造成的相同影響。  
  
 在擴充之 `FirstOrDefault` 呼叫的情況下，程式碼需要呼叫 `GetEnumerator()` 上的 <xref:System.Collections.Generic.IEnumerable%601>。  將 `symbols` 指派給 `enumerable` 類型的 `IEnumerable<Symbol>` 變數會遺失實際物件為 <xref:System.Collections.Generic.List%601> 的資訊。  這表示當程式碼擷取具有 `enumerable.GetEnumerator()` 的列舉值時，.NET Framework 必須以 Boxing 處理傳回結構，以指派給 `enumerator` 變數。  
  
 **範例 5 的修正**  
  
 修正方式是依照下列方式重寫 `FindMatchingSymbol`，以六行程式碼來取代一行程式碼，如此一來仍然簡潔易懂，並且容易維護。  
  
```csharp  
public Symbol FindMatchingSymbol(string name)  
    {  
        foreach (Symbol s in symbols)  
        {  
            if (s.Name == name)  
                return s;  
        }  
        return null;  
    }  
```  
  
 此程式碼不使用 LINQ 擴充方法、Lambdas 或列舉值，並且不會造成配置。  由於編譯器會將 `symbols` 集合視為 <xref:System.Collections.Generic.List%601>，並且可以將列舉值 (結構) 繫結至具有正確類型的區域變數，以避免 Boxing，因此不會有配置。  此函式的原始版本即為展示 C# 能力和 .NET Framework 生產力的絕佳範例。  此新的和更有效率的版本會保留這些品質，但不會加入要維護的任何複雜程式碼。  
  
### <a name="async-method-caching"></a>非同步方法快取  
 下一個範例顯示當您嘗試在[非同步](https://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7)方法中使用快取的結果時，所發生的常見問題。  
  
 **範例 6：在非同步方法中快取**  
  
 建置在新的 C# 和 Visual Basic 編譯器的 Visual Studio IDE 功能會經常擷取語法樹狀目錄，並且編譯器會以非同步方式來執行作業，以保持 Visual Studio 的回應能力。  以下是您可以撰寫以取得語法樹狀目錄之程式碼的第一個版本：  
  
```csharp  
class SyntaxTree { /*...*/ }  
  
class Parser { /*...*/  
    public SyntaxTree Syntax { get; }  
    public Task ParseSourceCode() { /*...*/ }  
}  
  
class Compilation { /*...*/  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 您會看到呼叫 `GetSyntaxTreeAsync()` 可具現化 `Parser`、剖析程式碼，然後傳回 <xref:System.Threading.Tasks.Task> 物件 `Task<SyntaxTree>`。  耗費大量資源的部分是配置 `Parser` 執行個體和剖析程式碼。  此函式傳回 <xref:System.Threading.Tasks.Task>，因此呼叫端可等候剖析運作，然後釋放 UI 執行緒以回應使用者輸入。  
  
 數項 Visual Studio 功能可能會嘗試取得同一個語法樹狀目錄，因此您可以撰寫下列程式碼快取剖析結果，以節省時間和配置。  不過，此程式碼會造成一項配置：  
  
```csharp  
class Compilation { /*...*/  
  
    private SyntaxTree cachedResult;  
  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        if (this.cachedResult == null)  
        {  
            var parser = new Parser(); // allocation  
            await parser.ParseSourceCode(); // expensive  
            this.cachedResult = parser.Syntax;  
        }  
        return this.cachedResult;  
    }  
}  
```  
  
 您會看到新程式碼具有內含名為 `SyntaxTree` 之 `cachedResult` 欄位的快取。  當此欄位為 null 時，`GetSyntaxTreeAsync()` 會執行工作並將結果儲存在快取中。  `GetSyntaxTreeAsync()` 會傳回 `SyntaxTree` 物件。  問題在於當您具有 `async` 類型的 `Task<SyntaxTree>` 函式，並傳回 `SyntaxTree` 類型的值時，編譯器會發出程式碼，配置一項 Task 以保存結果 (透過使用 `Task<SyntaxTree>.FromResult()`)。  此 Task 會標記為已完成，並會立即提供結果。  在新編譯器的程式碼中，已完成的 <xref:System.Threading.Tasks.Task> 物件經常出現，使得修正這些配置可大幅提升回應能力。  
  
 **範例 6 的修正**  
  
 若要移除已完成<xref:System.Threading.Tasks.Task>配置，您可以快取具有完成結果的 Task 物件：  
  
```csharp  
class Compilation { /*...*/  
  
    private Task<SyntaxTree> cachedResult;  
  
    public Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        return this.cachedResult ??   
               (this.cachedResult = GetSyntaxTreeUncachedAsync());  
    }  
  
    private async Task<SyntaxTree> GetSyntaxTreeUncachedAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 此程式碼將 `cachedResult` 的類型變更為 `Task<SyntaxTree>`，並採用 `async` Helper 函式來保存 `GetSyntaxTreeAsync()` 中的原始程式碼。  `GetSyntaxTreeAsync()` 現在使用 [null 聯合運算子](../../csharp/language-reference/operators/null-coalescing-operator.md)來傳回 `cachedResult` (如果不是 null)。  如果 `cachedResult` 為 null，則 `GetSyntaxTreeAsync()` 會呼叫 `GetSyntaxTreeUncachedAsync()` 並快取結果。  請注意，`GetSyntaxTreeAsync()` 不會像是程式碼的一般運作方式一樣，等候對 `GetSyntaxTreeUncachedAsync()` 的呼叫。  不使用 await 表示當 `GetSyntaxTreeUncachedAsync()` 傳回其 <xref:System.Threading.Tasks.Task> 物件時，`GetSyntaxTreeAsync()` 會立即傳回 <xref:System.Threading.Tasks.Task>。  現在，快取的結果是 <xref:System.Threading.Tasks.Task>，因此不會有傳回快取結果的配置。  
  
### <a name="additional-considerations"></a>其他考量  
 以下是有關大型應用程式或處理大量資料的應用程式可能發生之問題的一些重點。  
  
 **字典**  
  
 許多程式普遍都會用到字典，雖然字典很方便且本來就很有效率，  但經常遭到不當使用。  在 Visual Studio 和新編譯器中，分析顯示許多字典含有單一項目或為空的。  空的 <xref:System.Collections.Generic.Dictionary%602> 會含有十個欄位，並在 x86 電腦上佔用 48 個位元組的堆積。  當您需要透過定時查閱對應或關聯資料結構時，字典會很實用。  不過，當您只有幾個項目時，使用字典會浪費許多空間。  相反地，您可以反覆查看 `List<KeyValuePair\<K,V>>`，速度會一樣快。  如果使用字典只是為了下載並讀取資料 (很常見的模式)，根據您使用的項目數，搭配 N(log(N)) 查閱使用排序陣列可能幾乎會一樣快。  
  
 **類別與結構的比較**  
  
 類別和結構在調整應用程式時，一般或多或少都會耗費空間/時間。  類別在 x86 電腦上會產生 12 位元組的額外負荷，即使沒有欄位亦然，但是由於只會以一個指標來參考類別執行個體，因此傳遞時並不會耗費大量資源。  結構若未 Boxed，則不會造成堆積配置，但是當您將大型結構當做函式引數或傳回值傳遞時，需要 CPU 時間以自動複製結構的所有資料成員。  請留意對傳回結構之屬性的重複呼叫，並快取區域變數中的屬性值，以避免過多的資料複製。  
  
 **快取**  
  
 常用的效能訣竅是快取結果。  不過，沒有大小限制或處置原則的快取可能會造成記憶體流失。  處理大量資料時，如果您在快取中佔用大量記憶體，可能會導致記憶體回收，而使得快取查閱的優點無效。  
  
 在本文中，我們討論了您應該如何留意可能影響應用程式回應能力的效能瓶頸徵兆，特別是針對大型系統或處理大量資料的系統。 常見的原因包括 Boxing、字串操作、LINQ 和 Lambda、非同步方法中的快取、快取但不使用大小限制或處置原則、不當使用字典，以及在結構間傳遞。  請記住調整應用程式的四點事實：  
  
-   不要太早進行最佳化 - 保持生產力，並在發現問題時調整應用程式。  
  
-   程式碼剖析不會說謊 - 未經測量，不過是臆測。  
  
-   使用良好工具的成果大不相同 - 請下載並試用 PerfView。  
  
-   重點在於配置 - 這是編譯器平台小組花費最多時間提升新編譯器效能的地方。  
  
## <a name="see-also"></a>另請參閱

- [本主題的簡報影片](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)  
- [效能分析的初級開發人員指南](/visualstudio/profiling/beginners-guide-to-performance-profiling)  
- [效能](../../../docs/framework/performance/index.md)  
- [.NET 效能祕訣](https://msdn.microsoft.com/library/ms973839.aspx)  
- [Windows Phone Performance Analysis tool 工具](https://msdn.microsoft.com/magazine/hh781024.aspx)  
- [尋找與 Visual Studio Profiler 的應用程式瓶頸](https://msdn.microsoft.com/magazine/cc337887.aspx)  
- [Channel 9 PerfView 教學課程](https://channel9.msdn.com/Series/PerfView-Tutorial)  
- [.NET 編譯器平台 SDK](../../csharp/roslyn-sdk/index.md)
- [在 GitHub 上的 dotnet/roslyn 存放庫](https://github.com/dotnet/roslyn)

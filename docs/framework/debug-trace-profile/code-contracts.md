---
title: 程式碼合約
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code contracts
ms.assetid: 84526045-496f-489d-8517-a258cf76f040
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 721693166c561babb9d7825f480e92d14a5f347c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154433"
---
# <a name="code-contracts"></a>程式碼合約
程式碼合約可讓您指定程式碼中的前置條件、後置條件和物件非變異值。 前置條件是輸入方法或屬性時，必須符合的需求。 後置條件描述在方法或屬性程式碼結束時的期望。 物件非變異值描述針對處於良好狀態的類別，所預期的狀態。  
  
 程式碼合約包含用來標示程式碼的類別、用來進行編譯時期分析的靜態分析器，以及執行階段分析器。 您可以在 <xref:System.Diagnostics.Contracts> 命名空間中找到程式碼合約的類別。  
  
 程式碼合約的優點包括：  
  
-   改良的測試：程式碼合約提供靜態合約驗證、 執行階段檢查，以及文件產生。  
  
-   自動測試工具：您可以使用程式碼合約來產生更有意義的單元測試篩選出不符合前置條件的無意義的測試引數。  
  
-   靜態驗證：靜態檢查工具可以決定是否有任何合約違規，而不需要執行程式。 它會檢查隱含的合約，例如 null 取值和陣列界限，以及明確的合約。  
  
-   參考文件：文件產生器增強了現有的合約資訊的 XML 文件檔案。 此外，還有一些可搭配 [Sandcastle](https://github.com/EWSoftware/SHFB) 使用的樣式表，能夠讓產生的文件頁面具有合約區段。  
  
 所有 .NET Framework 語言都可以立即利用合約；您不必撰寫特殊的剖析器或編譯器。 Visual Studio 增益集可讓您指定所要執行之程式碼合約分析的層級。 分析器可以確認合約語式正確 (類型檢查和名稱解析)，並且可以產生 Microsoft 中繼語言 (MSIL) 格式合約的編譯形式。 在 Visual Studio 中撰寫合約，可讓您利用該工具所提供的標準 IntelliSense。  
  
 合約類別中的大部分方法都是有條件地編譯；也就是說，唯有當您使用 `#define` 指示詞，來定義特殊符號 CONTRACTS_FULL 時，編譯器才會發出呼叫至這些方法。 CONTRACTS_FULL 可讓您在程式碼中撰寫合約，而不需使用 `#ifdef` 指示詞；您可以產生不同的組建，有些有合約，有些則沒有。  
  
 如需使用程式碼協定的工具和詳細指示，請參閱 MSDN DevLabs 網站上的[程式碼合約](https://go.microsoft.com/fwlink/?LinkId=152461)。  
  
## <a name="preconditions"></a>前置條件  
 您可以使用 <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> 方法來表示前置條件。 前置條件可指定叫用方法時的狀態。 其通常是用來指定有效的參數值。 前置條件中提及之所有成員的可存取性，必須至少與方法本身相同，否則可能無法讓方法的所有呼叫端都了解該前置條件。 該條件必須沒有副作用。 失敗前置條件的執行階段行為，取決於執行階段分析器。  
  
 例如，下列前置條件表示 `x` 參數必須為非 null。  
  
 ```csharp
 Contract.Requires(x != null);
 ```
  
 如果您的程式碼必須在前置條件失敗時擲回特定例外狀況，您可以使用 <xref:System.Diagnostics.Contracts.Contract.Requires%2A> 的泛型多載，如下所示。  
  
 ```csharp
 Contract.Requires<ArgumentNullException>(x != null, "x");
 ```
  
### <a name="legacy-requires-statements"></a>舊版需要陳述式  
 大部分程式碼都包含 `if`-`then`-`throw` 程式碼形式的一些參數驗證。 在下列情況下，合約工具會將這些陳述式辨識為前置條件：  
  
-   這些陳述式會出現在方法中的任何其他陳述式之前。  
  
-   這一整組陳述式後面會接著明確的 <xref:System.Diagnostics.Contracts.Contract> 方法呼叫，例如呼叫 <xref:System.Diagnostics.Contracts.Contract.Requires%2A>、<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>、<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A> 或 <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> 方法。  
  
 當 `if`-`then`-`throw` 陳述式以這種形式出現時，工具會將其識別為舊版 `requires` 陳述式。 如果 `if`-`then`-`throw` 序列後面沒有接著任何其他合約，則以 <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> 方法來結束程式碼。  
  
```csharp
if (x == null) throw new ...
Contract.EndContractBlock(); // All previous "if" checks are preconditions
```
  
 請注意，先前測試中的條件是否定的前置條件。 (實際的前置條件是 `x != null`。)否定的前置條件是具有高度限制：必須在上一個範例中，所示撰寫也就是說，不應包含任何`else`子句，而且主體`then`子句必須是單一`throw`陳述式。 `if` 測試受限於單純性和可視性規則 (請參閱[使用方式方針](#usage_guidelines))，但是 `throw` 運算式只受限於單純性規則。 不過，所擲回之例外狀況的類型可視性，必須與發生合約的方法相同。  
  
## <a name="postconditions"></a>Postconditions  
 後置條件是當方法終止時的方法狀態合約。 在方法臨結束前，才會檢查後置條件。 失敗後置條件的執行階段行為，取決於執行階段分析器。  
  
 不同於前置條件，後置條件可能會參考可視性較低的成員。 用戶端可能無法使用私用狀態來了解或利用以後置條件來表示的一些資訊，但這不影響用戶端正確地使用方法的能力。  
  
### <a name="standard-postconditions"></a>標準後置條件  
 您可以使用 <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> 方法來表示後置條件。 後置條件會表示方法正常終止時，必須為 `true` 的條件。  
  
 ```csharp
 Contract.Ensures(this.F > 0);
 ```
  
### <a name="exceptional-postconditions"></a>例外後置條件  
 例外後置條件是當方法擲回特定例外狀況時，應為 `true` 的後置條件。 您可以使用 <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> 方法來指定這些後置條件，如下列範例所示。  
  
 ```csharp
 Contract.EnsuresOnThrow<T>(this.F > 0);
 ```
  
 此引數是每當擲回的例外狀況是 `T` 的子類型時，必須為 `true` 的條件。  
  
 有些例外狀況類型很難用在例外後置條件中。 例如，將類型 <xref:System.Exception> 用於 `T` 時，無論擲回的例外狀況類型為何，即使是堆疊溢位或其他無法控制的例外狀況，該方法都必須保證此條件。 例外後置條件應該只限用於呼叫成員時，可能會擲回的特定例外狀況；例如，針對 <xref:System.TimeZoneInfo> 方法呼叫擲回 <xref:System.InvalidTimeZoneException> 時。  
  
### <a name="special-postconditions"></a>特殊後置條件  
 下列方法僅限用於後置條件中：  
  
-   若要參考後置條件中的方法傳回值，您可以使用 `Contract.Result<T>()` 運算式，其中 `T` 要取代為方法的傳回類型。 當編譯器無法推斷類型時，您必須明確地提供類型。 例如，C#編譯器會無法推斷類型的方法不會接受任何引數，因此需要下列後置條件：`Contract.Ensures(0 <Contract.Result<int>())` 方法的傳回型別`void`不能參考`Contract.Result<T>()`其後置條件中。  
  
-   後置條件中的 prestate 值是指位於方法或屬性開頭之運算式的值。 它會使用 `Contract.OldValue<T>(e)` 運算式，其中 `T` 是 `e` 的類型。 只要編譯器能夠推斷其類型，您就可以省略泛型類型引數。 (例如，C# 編譯器一律會推斷類型，因為它會採用引數。)關於 `e` 中會發生什麼事，以及可能會出現舊運算式的內容，有幾項限制。 舊運算式不能包含另一個舊運算式。 最重要的是，舊的運算式必須參考存在於方法前置條件狀態中的值。 換句話說，只要方法的前置條件是 `true`，它就必須是可供評估的運算式。 以下是該規則的一些執行個體。  
  
    -   該值必須存在於方法的前置條件狀態中。 若要參考的物件上的欄位，前置條件必須保證該物件一律為非 null。  
  
    -   您不能在舊運算式中參考方法的傳回值：  
  
        ```csharp
        Contract.OldValue(Contract.Result<int>() + x) // ERROR  
        ```  
  
    -   您不能在舊運算式中參考 `out` 參數。  
  
    -   如果數量詞的範圍取決於方法的傳回值，則舊運算式不能取決於數量詞的繫結變數中：  
  
        ```csharp
        Contract.ForAll(0, Contract.Result<int>(), i => Contract.OldValue(xs[i]) > 3); // ERROR
        ```  
  
    -   舊運算式不能參考 <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> 或 <xref:System.Diagnostics.Contracts.Contract.Exists%2A> 呼叫中匿名委派的參數，除非是用來做為方法呼叫的索引子或引數：  
  
        ```csharp
        Contract.ForAll(0, xs.Length, i => Contract.OldValue(xs[i]) > 3); // OK
        Contract.ForAll(0, xs.Length, i => Contract.OldValue(i) > 3); // ERROR
        ```  
  
    -   如果舊運算式的值取決於匿名委派的任何參數，則舊運算式不能出現在匿名委派的主體中，除非匿名委派是 <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> 或 <xref:System.Diagnostics.Contracts.Contract.Exists%2A> 方法的引數：  
  
        ```csharp
        Method(... (T t) => Contract.OldValue(... t ...) ...); // ERROR
        ```  
  
    -   `Out` 參數出現問題，因為合約出現在方法的主體之前，而大部分編譯器不允許參考後置條件中的 `out` 參數。 為了解決這個問題，<xref:System.Diagnostics.Contracts.Contract> 類別提供了 <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> 方法，可允許以 `out` 參數為基礎的後置條件。  
  
        ```csharp
        public void OutParam(out int x)
        {
            Contract.Ensures(Contract.ValueAtReturn(out x) == 3);
            x = 3;
        }
        ```  
  
         如同 <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> 方法，只要編譯器能夠推斷其類型，您就可以省略泛型類型引數。 合約重寫器會將方法呼叫取代為 `out` 參數的值。 <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> 方法只會出現在後置條件中。 方法的引數必須是 `out` 參數，或是結構 `out` 參數的欄位。 參考結構建構函式後置條件中的欄位時，後者也很有用。  
  
        > [!NOTE]
        >  目前，程式碼合約分析工具不會檢查 `out` 參數是否正確初始化，並忽略其於後置條件中的相關記錄。 因此，在上述範例中，如果合約之後的字行使用 `x` 的值，而不是指派整數給它，則編譯器不會發出正確的錯誤。 不過，在未定義 CONTRACTS_FULL 前置處理器符號的組建 (例如 asa 發行組建) 上，編譯器會發出錯誤。  
  
## <a name="invariants"></a>非變異值  
 只要用戶端可以看到該物件，針對類別的每個執行個體，物件非變異值都是應該為 true 的條件。 在其表示的條件下，物件會被視為正確。  
  
 非變異方法會標示 <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> 屬性，以供識別。 非變異方法絕不能包含任何程式碼，但是對 <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> 方法的一連串呼叫除外，其中每個呼叫都會指定一個個別非變異值，如下列範例所示。  
  
```csharp
[ContractInvariantMethod]  
protected void ObjectInvariant ()   
{  
    Contract.Invariant(this.y >= 0);
    Contract.Invariant(this.x > this.y);
    ...
}
```  
  
 CONTRACTS_FULL 前置處理器符號會有條件地定義非變異值。 在執行階段檢查期間，會在每個公用方法的結尾檢查非變異值。 如果非變異值提及在相同類別中的公用方法，則會停用通常在該公用方法結尾進行的非變異檢查。 此檢查反而只會發生在該類別最外層的方法呼叫結尾。 如果因為呼叫另一個類別上的方法而重新輸入此類別，也會進行這項檢查。 物件完成項不會檢查非變異值和<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>實作。  
  
<a name="usage_guidelines"></a>   
## <a name="usage-guidelines"></a>用法方針  
  
### <a name="contract-ordering"></a>合約排序  
 下表顯示當您撰寫方法合約時，應該使用的項目順序。  
  
|`If-then-throw statements`|回溯相容公用前置條件|  
|-|-|  
|<xref:System.Diagnostics.Contracts.Contract.Requires%2A>|所有公用前置條件。|  
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|所有公用 (一般) 後置條件。|  
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|所有公用例外後置條件。|  
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|所有私用/內部 (一般) 後置條件。|  
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|所有私用/內部 (一般) 例外後置條件。|  
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|如果使用 `if`-`then`-`throw` 樣式前置條件，而沒有搭配任何其他合約，則呼叫 <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>，以指出所有先前的 if 檢查都是前置條件。|  
  
<a name="purity"></a>   
### <a name="purity"></a>單純性  
 在合約中呼叫的所有方法都必須都是單純的；也就是說，這些方法絕不能更新任何預先存在的狀態。 單純方法可以修改進入單純方法之後已建立的物件。  
  
 程式碼合約工具目前假設下列程式碼項目是單純的：  
  
-   標示 <xref:System.Diagnostics.Contracts.PureAttribute> 的方法。  
  
-   標示 <xref:System.Diagnostics.Contracts.PureAttribute> 的類型 (此屬性會套用至所有類型的方法)。  
  
-   屬性 get 存取子。  
  
-   運算子 (名稱開頭為 "op"，並且有一個或兩個參數以及非 void 傳回類型的靜態方法)。  
  
-   完整名稱開頭為 "System.Diagnostics.Contracts.Contract"、"System.String"、"System.IO.Path" 或 "System.Type" 的任何方法。  
  
-   任何叫用的委派，前提是委派類型本身是以 <xref:System.Diagnostics.Contracts.PureAttribute> 來屬性化。 委派類型 <xref:System.Predicate%601?displayProperty=nameWithType> 和 <xref:System.Comparison%601?displayProperty=nameWithType> 會被視為單純。  
  
<a name="visibility"></a>   
### <a name="visibility"></a>可視性  
 合約中提及之所有成員的可視性，必須至少與其所在的方法相同。 例如，針對公用方法，不能在前置條件中提及私用欄位；用戶端無法在呼叫該方法之前，先驗證這類合約。 不過，如果該欄位標示 <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>，則不受限於這些規則。  
  
## <a name="example"></a>範例  
 下列範例顯示程式碼合約的用法。  
  
 [!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
 [!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]

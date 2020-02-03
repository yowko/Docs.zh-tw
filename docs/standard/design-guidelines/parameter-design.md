---
title: 參數設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
ms.openlocfilehash: 78eb07503810e75d14bcd73740fe429e2f73475e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743671"
---
# <a name="parameter-design"></a>參數設計

本節提供有關參數設計的廣泛指導方針，包括包含檢查引數之指導方針的章節。 此外，您應該參考[具名引數](../../../docs/standard/design-guidelines/naming-parameters.md)中所述的指導方針。

 ✔️確實使用提供成員所需功能的最少衍生參數類型。

 例如，假設您想要設計一個列舉集合的方法，並將每個專案列印到主控台。 例如，這類方法應該採用 <xref:System.Collections.IEnumerable> 做為參數，而不是 <xref:System.Collections.ArrayList> 或 <xref:System.Collections.IList>。

 ❌ 不使用保留的參數。

 如果某些未來版本中需要更多的成員輸入，則可以加入新的多載。

 ❌ 沒有公開的方法，可接受指標、指標陣列或多維陣列做為參數。

 指標和多維陣列相對較難正確使用。 幾乎在所有情況下，都可以重新設計 Api，以避免將這些類型當做參數來採用。

 ✔️會將所有 `out` 參數都放在所有傳值和 `ref` 參數後面（不包括參數陣列），即使它導致多載之間的參數排序不一致（請參閱[成員](../../../docs/standard/design-guidelines/member-overloading.md)多載）。

 `out` 參數可視為額外的傳回值，並將它們分組在一起，讓方法簽章更容易瞭解。

 覆寫成員或執行介面成員時，✔️在具名引數中是一致的。

 這會更有效地傳達方法之間的關聯性。

### <a name="choose-between-enum-and-boolean-parameters"></a>選擇列舉和布林參數
 如果成員會有兩個或更多的布林參數，✔️確實使用列舉。

 除非您確定絕對不需要兩個以上的值，否則 ❌ 不使用布林值。

 列舉可讓您在未來新增值時提供一些空間，但您應該瞭解將值加入至列舉的所有含意，這些都是在[Enum 設計](../../../docs/standard/design-guidelines/enum.md)中所述。

 ✔️請考慮使用布林值做為真正雙州數值的函式參數，而且只會用來初始化布林屬性。

### <a name="validate-arguments"></a>驗證引數
 ✔️會驗證傳遞至公用、受保護或明確執行之成員的引數。 如果驗證失敗，則擲回 <xref:System.ArgumentException?displayProperty=nameWithType>或其中一個子類別。

 請注意，實際的驗證不一定要在公用或受保護的成員本身發生。 在某些私用或內部常式的較低層級，可能會發生此問題。 主要的重點是，向使用者公開的整個介面區都會檢查引數。

 如果傳遞 null 引數，而且成員不支援 null 引數，✔️ DO 會擲回 <xref:System.ArgumentNullException>。

 ✔️執行驗證列舉參數。

 「不要」假設列舉引數會在列舉所定義的範圍內。 CLR 允許將任何整數值轉換為列舉值，即使列舉中未定義此值。

 ❌ 不要使用 <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> 進行列舉範圍檢查。

 ✔️請注意，可變引數在驗證之後可能已變更。

 如果成員區分安全性，建議您建立複本，然後驗證和處理引數。

### <a name="pass-parameters"></a>傳遞參數
 從架構設計工具的觀點來看，有三個主要的參數群組：傳值參數、`ref` 參數和 `out` 參數。

 透過傳值參數傳遞引數時，成員會收到傳入的實際引數複本。 如果引數是實值型別，則引數的複本會放在堆疊上。 如果引數是參考型別，則會將參考的複本放在堆疊上。 最受歡迎的 CLR 語言， C#例如、Visual Basic 和C++，預設為以傳值方式傳遞參數。

 透過 `ref` 參數傳遞引數時，成員會收到傳入之實際引數的參考。 如果引數是實值型別，則引數的參考會放在堆疊上。 如果引數是參考型別，參考的參考會放在堆疊上。 `Ref` 參數可以用來允許成員修改呼叫者所傳遞的引數。

 `Out` 參數與 `ref` 參數類似，但有一些小差異。 參數最初被視為未指派，而且在指派某個值之前，無法在成員主體中讀取。 此外，必須在成員傳回之前，先指派一些值給參數。

 ❌ 避免使用 `out` 或 `ref` 參數。

 使用 `out` 或 `ref` 參數需要有指標的經驗、瞭解實數值型別和參考型別之間的差異，以及處理具有多個傳回值的方法。 此外，`out` 和 `ref` 參數之間的差異並不廣泛瞭解。 一般物件的架構架構設計人員應該不會預期使用者會使用 `out` 或 `ref` 參數來主控。

 ❌ 不要以傳址方式傳遞參考型別。

 規則有一些有限的例外狀況，例如可以用來交換參考的方法。

### <a name="members-with-variable-number-of-parameters"></a>具有可變參數數目的成員
 可以接受可變數目引數的成員會藉由提供陣列參數來表示。 例如，<xref:System.String> 提供下列方法：

```csharp
public class String {
    public static string Format(string format, object[] parameters);
}
```

 然後，使用者可以呼叫 <xref:System.String.Format%2A?displayProperty=nameWithType> 方法，如下所示：

 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`

 將C# params 關鍵字新增至陣列參數會將參數變更為所謂的 params 陣列參數，並提供建立暫存陣列的快捷方式。

```csharp
public class String {
    public static string Format(string format, params object[] parameters);
}
```

 這麼做可讓使用者直接在引數清單中傳遞陣列元素，藉以呼叫方法。

 `String.Format("File {0} not found in {1}",filename,directory);`

 請注意，params 關鍵字只能加入至參數清單中的最後一個參數。

 如果您預期使用者會傳遞包含少量元素的陣列，✔️請考慮將 params 關鍵字新增至陣列參數。 如果預期會在常見的案例中傳遞許多元素，則使用者可能不會以內嵌方式傳遞這些專案，因此不需要 params 關鍵字。

 如果呼叫端幾乎一律具有陣列中的輸入，❌ 避免使用 params 陣列。

 例如，具有位元組陣列參數的成員幾乎不會藉由傳遞個別位元組來呼叫。 因此，.NET Framework 中的位元組陣列參數不會使用 params 關鍵字。

 如果接受 params 陣列參數的成員修改陣列，❌ 不使用 params 陣列。

 因為許多編譯器會將成員的引數轉換成呼叫位置的臨時陣列，所以陣列可能是暫存物件，因此對陣列所做的任何修改都將遺失。

 ✔️請考慮在簡單的多載中使用 params 關鍵字，即使較複雜的多載無法使用它也一樣。

 詢問您是否要讓使用者在一個多載中具有 params 陣列值，即使它不在所有多載中也一樣。

 ✔️請嘗試排序參數，讓它可以使用 params 關鍵字。

 ✔️請考慮提供特殊的多載和程式碼路徑，以在極具效能的 Api 中有少量引數的呼叫。

 如此一來，當使用少數引數呼叫 API 時，就可以避免建立陣列物件。 藉由取得陣列參數的單數形式並加上數值後置詞，來形成參數的名稱。

 只有在您要特別使用整個程式碼路徑時，才應該這麼做，而不只是建立陣列並呼叫更通用的方法。

 ✔️請注意，null 可以當做 params 陣列引數傳遞。

 在處理之前，您應該先驗證陣列不是 null。

 ❌ 不使用 `varargs` 方法，也稱為省略號。

 某些 CLR 語言（例如C++）支援傳遞變數參數清單的替代慣例，稱為 `varargs` 方法。 慣例不應用於架構中，因為它不符合 CLS 標準。

### <a name="pointer-parameters"></a>指標參數
 一般而言，指標不應該出現在設計良好的 managed 程式碼架構的公用介面區中。 在大部分的情況下，都應該封裝指標。 不過，在某些情況下，指標是基於互通性的原因，而在這種情況下使用指標是適當的。

 ✔️確實提供接受指標引數之任何成員的替代方式，因為指標不符合 CLS 標準。

 ❌ 避免對指標引數進行昂貴的引數檢查。

 ✔️在使用指標設計成員時，請遵循常見的指標相關慣例。

 例如，不需要傳遞開始索引，因為可以使用簡單的指標算術來達到相同的結果。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition[ 節錄。](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)*

## <a name="see-also"></a>另請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

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
author: KrzysztofCwalina
ms.openlocfilehash: 28b00f5911bb47536ec44b96f284e47b6c671149
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353738"
---
# <a name="parameter-design"></a>參數設計
本節提供有關參數設計的廣泛指導方針，包括包含檢查引數之指導方針的章節。 此外，您應該參考[具名引數](../../../docs/standard/design-guidelines/naming-parameters.md)中所述的指導方針。  
  
 **✓ DO** 使用至少衍生的參數類型，提供成員所需的功能。  
  
 例如，假設您想要設計一個列舉集合的方法，並將每個專案列印到主控台。 例如，這類方法應該以 <xref:System.Collections.IEnumerable> 做為參數，而不是 <xref:System.Collections.ArrayList> 或 <xref:System.Collections.IList>。  
  
 **X DO NOT** 使用保留的參數。  
  
 如果某些未來版本中需要更多的成員輸入，則可以加入新的多載。  
  
 **X DO NOT** 有公開這些方法會採用指標、 陣列的指標或做為參數的多維度陣列。  
  
 指標和多維陣列相對較難正確使用。 幾乎在所有情況下，都可以重新設計 Api，以避免將這些類型當做參數來採用。  
  
 **✓ DO** 放置所有 `out` 遵循所有由值參數和 `ref` 參數 （不含參數陣列），即使它會造成不一致的參數多載之間的順序 (請參閱 [成員多載 ](../../../docs/standard/design-guidelines/member-overloading.md))。  
  
 @No__t-0 參數可以視為額外的傳回值，並將它們分組在一起，讓方法簽章更容易瞭解。  
  
 **✓ DO** 一致時覆寫成員命名的參數，或實作介面成員中。  
  
 這會更有效地傳達方法之間的關聯性。  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a>選擇列舉和布林值參數  
 **✓ DO** 如果成員原本必須另外兩個或多個布林值參數使用的列舉。  
  
 **X DO NOT** 使用布林值，除非您完全確定永遠不會需要兩個以上的值。  
  
 列舉可讓您在未來新增值時提供一些空間，但您應該瞭解將值加入至列舉的所有含意，這些都是在[Enum 設計](../../../docs/standard/design-guidelines/enum.md)中所述。  
  
 **✓ CONSIDER** 使用建構函式參數是真正的兩個狀態的值，只會用來初始化布林值屬性的布林值。  
  
### <a name="validating-arguments"></a>驗證引數  
 **✓ DO** 驗證引數傳遞至 public、 protected 或明確實作的成員。 如果驗證失敗，則擲回 <xref:System.ArgumentException?displayProperty=nameWithType> 或它的其中一個子類別。  
  
 請注意，實際的驗證不一定要在公用或受保護的成員本身發生。 在某些私用或內部常式的較低層級，可能會發生此問題。 主要的重點是，向使用者公開的整個介面區都會檢查引數。  
  
 **✓ DO** 擲回 <xref:System.ArgumentNullException> 如果傳遞 null 引數，而且成員不支援 null 引數。  
  
 **✓ DO** 驗證列舉的參數。  
  
 「不要」假設列舉引數會在列舉所定義的範圍內。 CLR 允許將任何整數值轉換為列舉值，即使列舉中未定義此值。  
  
 **X DO NOT** 使用 <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> 列舉範圍檢查。  
  
 **✓ DO** 注意之後他們已驗證，可能已經變更可變動的引數。  
  
 如果成員區分安全性，建議您建立複本，然後驗證和處理引數。  
  
### <a name="parameter-passing"></a>參數傳遞  
 從架構設計工具的觀點來看，有三個主要的參數群組：傳值參數、@no__t 0 參數和 @no__t 1 參數。  
  
 透過傳值參數傳遞引數時，成員會收到傳入的實際引數複本。 如果引數是實值型別，則引數的複本會放在堆疊上。 如果引數是參考型別，則會將參考的複本放在堆疊上。 最受歡迎的 CLR 語言， C#例如、VB.NET 和C++，預設為以傳值方式傳遞參數。  
  
 透過 `ref` 參數傳遞引數時，成員會收到傳入之實際引數的參考。 如果引數是實值型別，則引數的參考會放在堆疊上。 如果引數是參考型別，參考的參考會放在堆疊上。 `Ref` 參數可以用來允許成員修改呼叫者所傳遞的引數。  
  
 `Out` 參數類似于 `ref` 參數，但有一些小差異。 參數最初被視為未指派，而且在指派某個值之前，無法在成員主體中讀取。 此外，必須在成員傳回之前，先指派一些值給參數。  
  
 **X AVOID** 使用 `out` 或 `ref` 參數。  
  
 使用 `out` 或 @no__t 1 參數需要使用指標的經驗、瞭解實數值型別和參考型別之間的差異，以及處理具有多個傳回值的方法。 此外，和`ref`參數之間`out`的差異也無法廣泛瞭解。 一般物件的架構架構設計人員應該不會預期使用者會使用 `out` 或 @no__t 1 參數來主控。  
  
 **X DO NOT** 傳址方式傳遞參考型別。  
  
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
  
 **✓ CONSIDER** params 關鍵字加入陣列參數，如果您預期使用者會傳遞具有少數的元素的陣列。 如果預期會在常見的案例中傳遞許多元素，則使用者可能不會以內嵌方式傳遞這些專案，因此不需要 params 關鍵字。  
  
 **X AVOID** 使用參數陣列，如果呼叫端會幾乎都已經輸入陣列中。  
  
 例如，具有位元組陣列參數的成員幾乎不會藉由傳遞個別位元組來呼叫。 因此，.NET Framework 中的位元組陣列參數不會使用 params 關鍵字。  
  
 **X DO NOT** 使用參數陣列，如果陣列修改採取 params 陣列參數的成員。  
  
 因為許多編譯器會將成員的引數轉換成呼叫位置的臨時陣列，所以陣列可能是暫存物件，因此對陣列所做的任何修改都將遺失。  
  
 **✓ CONSIDER** 使用 params 關鍵字，在簡單的多載中，即使有更複雜的多載無法使用。  
  
 詢問您是否要讓使用者在一個多載中具有 params 陣列值，即使它不在所有多載中也一樣。  
  
 **✓ DO** 嘗試順序參數，讓它能夠使用 params 關鍵字。  
  
 **✓ CONSIDER** 小極為重視效能的應用程式開發介面中的引數數目的呼叫中提供特殊的多載，程式碼路徑。  
  
 如此一來，當使用少數引數呼叫 API 時，就可以避免建立陣列物件。 藉由取得陣列參數的單數形式並加上數值後置詞，來形成參數的名稱。  
  
 只有在您要特別使用整個程式碼路徑時，才應該這麼做，而不只是建立陣列並呼叫更通用的方法。  
  
 **✓ DO** 注意可以當成參數陣列引數傳遞的 null。  
  
 在處理之前，您應該先驗證陣列不是 null。  
  
 **X DO NOT** 使用 `varargs` 方法，否則會以省略符號。  
  
 某些 CLR 語言（例如C++）支援傳遞變數參數清單的替代慣例，稱為 @no__t 1 方法。 慣例不應用於架構中，因為它不符合 CLS 標準。  
  
### <a name="pointer-parameters"></a>指標參數  
 一般而言，指標不應該出現在設計良好的 managed 程式碼架構的公用介面區中。 在大部分的情況下，都應該封裝指標。 不過，在某些情況下，指標是基於互通性的原因，而在這種情況下使用指標是適當的。  
  
 **✓ DO** 適用於任何會使用指標引數的成員提供的替代方案，因為不符合 CLS 標準的指標。  
  
 **X AVOID** 執行耗費資源檢查指標引數的引數。  
  
 **✓ DO** 設計具有指標的成員時，請遵循一般指標相關的慣例。  
  
 例如，不需要傳遞開始索引，因為可以使用簡單的指標算術來達到相同的結果。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 從 @no__t 1Framework 設計指導方針中，@no__t 0Reprinted by 皮耳森教育，Inc. 的許可權：可重複使用的 .NET 程式庫、第2版 @ no__t-0 by Krzysztof Cwalina 和 Brad Abrams 的慣例、慣用語和模式，已于2008年10月22日發行，其為 Microsoft Windows 開發系列的一部分 Addison-Wesley Professional。 *  
  
## <a name="see-also"></a>另請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

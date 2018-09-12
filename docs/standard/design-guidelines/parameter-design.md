---
title: 參數設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea5311de8cef266af23b259d943568bfa95eaf72
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44493923"
---
# <a name="parameter-design"></a>參數設計
本章節會提供廣泛的指導方針，在參數的設計，包括各節來檢查引數的指導方針。 此外，您應該參閱中所述的指導方針[命名的參數](../../../docs/standard/design-guidelines/naming-parameters.md)。  
  
 **✓ DO** 使用至少衍生的參數類型，提供成員所需的功能。  
  
 例如，假設您想要設計的方法，列舉集合，並會列印到主控台的每個項目。 這種方法花費<xref:System.Collections.IEnumerable>做為參數，不<xref:System.Collections.ArrayList>或<xref:System.Collections.IList>，例如。  
  
 **X DO NOT** 使用保留的參數。  
  
 如果某些未來的版本中需要更多輸入才能成員，就可以加入新的多載。  
  
 **X DO NOT** 有公開這些方法會採用指標、 陣列的指標或做為參數的多維度陣列。  
  
 指標和多維度陣列是相對較難適當地使用。 在幾乎所有的情況下，就可以重新設計 Api 避免這些類型做為參數。  
  
 **✓ DO** 放置所有 `out` 遵循所有由值參數和 `ref` 參數 （不含參數陣列），即使它會造成不一致的參數多載之間的順序 (請參閱 [成員多載 ](../../../docs/standard/design-guidelines/member-overloading.md))。  
  
 `out`參數可視為額外的傳回值，並將它們群組在一起會更容易了解的方法簽章。  
  
 **✓ DO** 一致時覆寫成員命名的參數，或實作介面成員中。  
  
 這會進一步通訊方法之間的關聯性。  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a>選擇列舉或布林值參數  
 **✓ DO** 如果成員原本必須另外兩個或多個布林值參數使用的列舉。  
  
 **X DO NOT** 使用布林值，除非您完全確定永遠不會需要兩個以上的值。  
  
 列舉會提供一些的空間，以便未來加入值，但是您應該注意將值加入至列舉中所述的所有的含意[列舉設計](../../../docs/standard/design-guidelines/enum.md)。  
  
 **✓ CONSIDER** 使用建構函式參數是真正的兩個狀態的值，只會用來初始化布林值屬性的布林值。  
  
### <a name="validating-arguments"></a>驗證引數  
 **✓ DO** 驗證引數傳遞至 public、 protected 或明確實作的成員。 擲回<xref:System.ArgumentException?displayProperty=nameWithType>，或其中一個子類別，如果驗證失敗。  
  
 請注意，實際的驗證不一定要在公用或受保護成員本身中。 它可能會發生一些私用或內部的常式中較低層級。 主要的重點是公開給使用者的整個介面區檢查引數。  
  
 **✓ DO** 擲回 <xref:System.ArgumentNullException> 如果傳遞 null 引數，而且成員不支援 null 引數。  
  
 **✓ DO** 驗證列舉的參數。  
  
 請勿假設列舉引數會在列舉所定義的範圍。 CLR 可讓轉換任何整數值轉換為列舉值，即使值未定義的列舉中。  
  
 **X DO NOT** 使用 <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> 列舉範圍檢查。  
  
 **✓ DO** 注意之後他們已驗證，可能已經變更可變動的引數。  
  
 如果成員是機密的安全性，即建議來建立複本，然後驗證和處理引數。  
  
### <a name="parameter-passing"></a>參數傳遞  
 從架構設計師的觀點來看，有三個參數的主要群組： 藉由值參數`ref`參數，和`out`參數。  
  
 透過傳值參數傳遞的引數時，該成員就會收到一份在傳遞的實際引數。 如果引數是實值型別，會將引數的複本放在堆疊上。 如果引數是參考型別，參考的複本放在堆疊上。 最受歡迎 CLR 語言，例如 C#、 VB.NET 和 c + +，以傳值方式傳遞參數的預設值。  
  
 引數傳遞時`ref`參數，該成員收到傳入的實質引數的參考。 引數是實值型別，引數的參考會放在堆疊上。 引數是參考型別，參考的參考會放在堆疊上。 `Ref` 參數可用來允許修改由呼叫端傳遞的引數的成員。  
  
 `Out` 參數是類似於`ref`參數，但有一些小差異。 參數一開始被視為未設定，並且無法在指派一些值之前讀取成員主體中。 此外，參數有成員傳回之前指派一些值。  
  
 **X AVOID** 使用 `out` 或 `ref` 參數。  
  
 使用`out`或`ref`參數需要經驗指標了實值型別和參考型別之間的差異，並處理具有多個傳回值的方法。 此外，之間的差異`out`和`ref`參數不廣泛了解。 Framework 設計適合一般觀眾的架構設計人員不應該預期使用者會熟練地運用`out`或`ref`參數。  
  
 **X DO NOT** 傳址方式傳遞參考型別。  
  
 有一些規則，例如可以用來交換參考方法的有限例外狀況。  
  
### <a name="members-with-variable-number-of-parameters"></a>使用變動數目的參數的成員  
 可以接受可變數目的引數的成員會藉由提供的陣列參數來表示。 比方說，<xref:System.String>提供下列方法：  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 使用者接著可以呼叫<xref:System.String.Format%2A?displayProperty=nameWithType>方法，如下所示：  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 加入的陣列參數中的 C# params 關鍵字對所謂的 params 陣列參數中的參數，並提供捷徑，以建立暫存陣列。  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 如此一來，可讓使用者藉由傳遞陣列元素的引數清單中的直接呼叫方法。  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 請注意，params 關鍵字可以只能加入至參數清單中的最後一個參數。  
  
 **✓ CONSIDER** params 關鍵字加入陣列參數，如果您預期使用者會傳遞具有少數的元素的陣列。 如果預期的許多項目將會收到在一般案例，使用者，可能無法通過這些內嵌的項目，因此不需要 params 關鍵字。  
  
 **X AVOID** 使用參數陣列，如果呼叫端會幾乎都已經輸入陣列中。  
  
 比方說，成員使用位元組陣列參數幾乎不會呼叫傳遞個別的位元組。 基於這個理由，在.NET Framework 中的位元組陣列參數請勿使用 params 關鍵字。  
  
 **X DO NOT** 使用參數陣列，如果陣列修改採取 params 陣列參數的成員。  
  
 事實上，許多編譯器會將該成員的引數轉換成暫存陣列呼叫位置，因為陣列可能是暫存物件，，因此陣列的任何修改可能會遺失。  
  
 **✓ CONSIDER** 使用 params 關鍵字，在簡單的多載中，即使有更複雜的多載無法使用。  
  
 問問自己的使用者會有參數陣列中其中一個多載，即使它不是在所有多載來值。  
  
 **✓ DO** 嘗試順序參數，讓它能夠使用 params 關鍵字。  
  
 **✓ CONSIDER** 小極為重視效能的應用程式開發介面中的引數數目的呼叫中提供特殊的多載，程式碼路徑。  
  
 如此可避免使用少量的引數呼叫 API 時，建立陣列物件。 將陣列參數的單數形式，並將數值後置詞，以形成參數的名稱。  
  
 您應該只能這麼想以特殊案例的完整程式碼路徑，不只是建立陣列，並呼叫的較通用的方法。  
  
 **✓ DO** 注意可以當成參數陣列引數傳遞的 null。  
  
 您應該驗證陣列不是 null 處理之前。  
  
 **X DO NOT** 使用 `varargs` 方法，否則會以省略符號。  
  
 某些 CLR 語言，例如 c + + 支援替代的慣例來傳遞呼叫的變數參數清單`varargs`方法。 慣例不應在架構，因為它不符合 CLS 標準。  
  
### <a name="pointer-parameters"></a>指標參數  
 一般情況下，指標不應該出現在設計良好的 managed 程式碼架構的公用表面區域。 大部分的情況下，應該封裝的指標。 不過，在某些情況下，指標所需的互通性考量，並且適合在此情況下使用指標。  
  
 **✓ DO** 適用於任何會使用指標引數的成員提供的替代方案，因為不符合 CLS 標準的指標。  
  
 **X AVOID** 執行耗費資源檢查指標引數的引數。  
  
 **✓ DO** 設計具有指標的成員時，請遵循一般指標相關的慣例。  
  
 比方說，沒有必要將起始的索引，因為可以使用簡單指標算術來達到相同的結果。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)  
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

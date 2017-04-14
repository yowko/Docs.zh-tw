---
title: "參數設計 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "成員設計方針 [.NET Framework] 參數"
  - "成員 [.NET Framework] 參數"
  - "名稱 [.NET Framework] 參數"
  - "參數，設計方針"
  - "保留的參數"
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 參數設計
本節提供廣泛的指導方針參數設計，包括各節來檢查引數的指導方針。 此外，您應該參考中所述的指導方針 [命名參數](../../../docs/standard/design-guidelines/naming-parameters.md)。  
  
 **✓ 執行** 使用最低的衍生參數類型，提供成員所需的功能。  
  
 例如，假設您想要設計的方法，列舉集合，並列印到主控台的每個項目。 這種方法應該採用 <xref:System.Collections.IEnumerable> 做為參數，不 <xref:System.Collections.ArrayList> 或 <xref:System.Collections.IList>, ，例如。  
  
 **X 不** 使用保留的參數。  
  
 如果需要更多成員的輸入一些未來的版本，可以加入新的多載。  
  
 **X 不** 有公開採用指標、 陣列的指標或做為參數的多維陣列的方法。  
  
 指標和多維度陣列是很難適當地使用。 在大多數情況下，Api 可以重新設計，若要避免採用這些做為參數的型別。  
  
 **✓ 執行** 放置所有 `out` 所有由值參數和 `ref` 參數 （不包括參數陣列），即使它會造成不一致的多載之間的排序參數 \(請參閱 [成員多載](../../../docs/standard/design-guidelines/member-overloading.md)\)。  
  
 `out` 參數都可視為額外的傳回值，並將它們群組在一起讓方法簽名碼更容易了解。  
  
 **✓ 執行** 時覆寫成員命名的參數或實作介面成員中保持一致。  
  
 這會進一步通訊方法之間的關聯性。  
  
### 列舉和布林值參數之間選擇  
 **✓ 執行** 使用列舉的成員否則會有兩個或多個布林值參數。  
  
 **X 不** 使用布林值，除非您真的確定永遠不會需要兩個以上的值。  
  
 列舉會提供一些空間，以便未來加入值，但是您應該留意將值加入至列舉，如下所述的所有問題 [列舉設計](../../../docs/standard/design-guidelines/enum.md)。  
  
 **✓ 考慮** 使用建構函式參數是真正的兩個狀態的值，只是用來初始化布林值屬性的布林值。  
  
### 驗證引數  
 **✓ 執行** 驗證引數傳遞至公用、 受保護，或明確實作的成員。 擲回 <xref:System.ArgumentException?displayProperty=fullName>, ，或其中一個子類別，如果驗證失敗。  
  
 請注意，實際的驗證不一定要在公用或受保護成員本身中。 它可能會發生一些私用或內部常式中較低層級。 主要的重點是公開給使用者的整個介面區域會檢查引數。  
  
 **✓ 執行** 擲回 <xref:System.ArgumentNullException> 如果傳遞 null 引數，而且成員不支援 null 引數。  
  
 **✓ 執行** 驗證列舉的參數。  
  
 請勿假設 enum 引數會列舉所定義的範圍中。 CLR 可讓任何整數值轉換成列舉值，即使列舉中未定義的值。  
  
 **X 不** 使用 <xref:System.Enum.IsDefined%2A?displayProperty=fullName> 列舉範圍檢查。  
  
 **✓ 執行** 注意之後都在進行驗證，可能已經變更可變引數。  
  
 如果成員是機密的安全性，也鼓勵複製然後驗證並處理引數。  
  
### 參數傳遞  
 從架構設計師的觀點來看，有三個參數的主要群組︰ 由值參數， `ref` 參數，和 `out` 參數。  
  
 傳遞引數是透過由值參數，該成員會收到一份中傳遞的實際引數。 如果引數是實值型別，引數的複本放在堆疊上。 如果引數是參考型別，會將參考的複本放在堆疊上。 最受歡迎 CLR 語言，例如 C\#、 VB.NET 和 c \+ \+，以傳值方式傳遞參數的預設值。  
  
 當引數傳遞到 `ref` 參數，該成員會接收傳入的實質引數的參考。 如果引數是實值型別，引數的參考會放在堆疊上。 如果引數是參考型別，參考的參考會放在堆疊上。`Ref` 參數可以用來允許修改由呼叫端傳遞引數的成員。  
  
 `Out` 參數是類似於 `ref` 參數，但有一些小差異。 參數一開始會視為未設定，並且會指派一些值之前無法讀取成員主體中。 此外，參數有成員傳回之前指派一些值。  
  
 **X 避免** 使用 `out` 或 `ref` 參數。  
  
 使用 `out` 或 `ref` 參數需要接觸指標了實值型別和參考型別之間的差異，並處理具有多個傳回值的方法。 此外，之間的差異 `out` 和 `ref` 參數不廣泛了解。 架構設計目標為一般使用者的架構設計人員不應預期使用者會熟練地運用到 `out` 或 `ref` 參數。  
  
 **X 不** 傳址方式傳遞參考類型。  
  
 有一些限制的例外狀況規則，例如，可用來交換參考的方法。  
  
### 成員具有不定數目參數  
 可變數目的引數的成員會藉由提供的陣列參數來表示。 例如， <xref:System.String> 提供下列方法︰  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 使用者接著可以呼叫 <xref:System.String.Format%2A?displayProperty=fullName> 方法，如下所示︰  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 將 C\# params 關鍵字加入至陣列參數變成所謂的 params 陣列參數的參數，並提供建立暫存陣列的捷徑。  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 這樣做可讓使用者藉由傳遞陣列元素的引數清單中的直接呼叫方法。  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 請注意，可以在參數清單中的最後一個參數，才能加入 params 關鍵字。  
  
 **✓ 考慮** params 關鍵字加入陣列參數，如果您預期使用者會傳遞具有較少的項目陣列。 如果預期的大量項目將會傳遞通用案例，使用者，可能無法通過這些項目內嵌，所以不需要 params 關鍵字。  
  
 **X 避免** 使用 params 陣列，如果呼叫端會幾乎已經輸入陣列中。  
  
 比方說，使用位元組陣列參數的成員幾乎永遠不會將呼叫傳遞個別的位元組。 基於這個理由，.NET Framework 中的位元組陣列參數請勿使用 params 關鍵字。  
  
 **X 不** 使用 params 陣列，如果陣列修改採取 params 陣列參數的成員。  
  
 由於許多編譯器，開啟上呼叫站台的暫存陣列成員的引數的事實，可能是暫存物件、 陣列，因此陣列的任何修改將會遺失。  
  
 **✓ 考慮** 使用 params 關鍵字，在簡單的多載中，即使更複雜的多載無法使用。  
  
 問問自己，是否使用者想值 params 陣列有一個多載中，即使它不是所有多載中。  
  
 **✓ 執行** 嘗試順序參數，讓它能夠使用 params 關鍵字。  
  
 **✓ 考慮** 小極為重視效能的 Api 中的引數數目的呼叫中提供特殊的多載和程式碼路徑。  
  
 這可以避免建立陣列物件，具有較少的引數呼叫 API 時。 取得陣列參數的單數形式，並加入數值後置詞，以形成參數的名稱。  
  
 您才應該這樣如果您要以特殊案例的完整程式碼路徑，不只是建立陣列，並呼叫更一般的方法。  
  
 **✓ 執行** 注意可以當成參數陣列引數傳遞的 null。  
  
 您應該驗證陣列不是 null 處理之前。  
  
 **X 不** 使用 `varargs` 方法，否則會以省略符號。  
  
 某些 CLR 語言，例如 c \+ \+ 支援替代的慣例來傳遞呼叫的可變個數參數清單 `varargs` 方法。 慣例不應用於架構，因為它不符合 CLS 標準。  
  
### 指標參數  
 一般情況下，指標不應該出現在設計良好的 managed 程式碼架構的公用表面區域。 大部分的情況下，應該封裝的指標。 不過，在某些情況下，指標所需的互通性考量，而且適合在此情況下使用指標。  
  
 **✓ 執行** 使用指標引數，任何成員提供的替代方式，因為指標並不符合 CLS 標準。  
  
 **X 避免** 進行昂貴檢查指標引數的引數。  
  
 **✓ 執行** 設計具有指標的成員時，請遵循一般指標相關的慣例。  
  
 例如，沒有必要傳遞的起始索引，因為簡單的指標算術可以用來達到相同的結果。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [成員設計方針](../../../docs/standard/design-guidelines/member.md)   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
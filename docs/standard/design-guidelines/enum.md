---
title: 列舉設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dea187b5f3911114e551d640e0bb0aa6fac1143
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213286"
---
# <a name="enum-design"></a>列舉設計
列舉都是一種特殊的實值型別。 有兩種類型的列舉： 簡單列舉和旗標的列舉。  
  
 簡單列舉代表封閉的少量的選擇。 簡單列舉的常見範例是一組色彩。  
  
 旗標列舉被設計來支援列舉值的位元運算。 旗標列舉的常見範例是選項的清單。  
  
 **✓ DO** 列舉使用強型別參數、 屬性和傳回值，表示一組值。  
  
 **✓ DO** 偏好使用列舉，而不靜態的常數。  
  
 **X DO NOT** 列舉用於開啟設定 （例如作業系統版本、 您的朋友、 等等的名稱。）。  
  
 **X DO NOT** 提供保留的列舉值是要供未來使用。  
  
 您一律只可以加入至現有的列舉的值，在稍後的階段。 請參閱[新增的值，以列舉](#add_value)如需詳細資訊將值加入至列舉。 保留的值只會干擾的一組真實的值，並通常會導致使用者錯誤。  
  
 **X AVOID** 公開僅有一個值的列舉。  
  
 確保未來的擴充性的 C Api 的常見作法是將保留的參數新增至方法簽章。 這類保留的參數可以表示為單一的預設值的列舉。 這不應該在受管理的 Api。 方法多載，可讓新增參數在未來的版本。  
  
 **X DO NOT** sentinel 值包含在列舉中。  
  
 雖然它們有時會很有幫助架構開發人員，sentinel 值會是令人困惑的 framework 的使用者。 它們用來追蹤狀態的列舉，而不是其中一個值是從列舉所表示的集合。  
  
 **✓ DO** 提供簡單列舉上零的值。  
  
 請考慮呼叫值類似"None"。 如果這類值不適用於這個特定的列舉，最常見的預設值，列舉應該指派基礎值為零。  
  
 **✓ CONSIDER** 使用 <xref:System.Int32> （大部分的程式設計語言中的預設值） 列舉的基礎類型為除非有下列情況：  
  
-   列舉是旗標列舉，而且您有 32 個以上的旗標，或希望有更多在未來。  
  
-   基礎類型必須是不同於<xref:System.Int32>更容易與預期不同大小列舉的 unmanaged 程式碼的互通性。  
  
-   較小的基礎類型會導致大量節省空間。 如果您預期的列舉，主要是做為控制流程的引數，則大小會將些許差異。 節省大小可能會很大如果：  
  
    -   您預期的列舉，用於經常執行個體化的結構或類別中的欄位。  
  
    -   您預期使用者建立大型陣列或集合的列舉執行個體。  
  
    -   您預期大量的列舉，可序列化的執行個體。  
  
 記憶體使用量，請留意，受管理的物件都`DWORD`-對齊，因此您實際上需要多個列舉或其他封裝具有較小的列舉，而以深遠的影響，因為總執行個體的大小一律為執行個體中的小型結構要無條件進位至`DWORD`。  
  
 **✓ DO** 命名為旗標列舉的複數名詞或名詞片語，並使用單數名詞或名詞片語的簡單列舉。  
  
 **X DO NOT** 擴充 <xref:System.Enum?displayProperty=nameWithType> 直接。  
  
 <xref:System.Enum?displayProperty=nameWithType> 是一種特殊類型用於由 CLR 建立使用者定義的列舉型別。 大部分的程式設計語言提供這項功能可讓您存取的程式設計項目。 例如，在 C#`enum`關鍵字用以定義列舉類型。  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a>設計的旗標列舉  
 **✓ DO** 套用 <xref:System.FlagsAttribute?displayProperty=nameWithType> 用於旗標列舉。 不套用這個屬性用於簡單的列舉。  
  
 **✓ DO** 使用的 2 乘冪的旗標列舉值，因此也可以自由地結合使用位元 OR 運算。  
  
 **✓ CONSIDER** 常提供的特殊的列舉值使用的旗標的組合。  
  
 位元運算是進階的概念，而且應該不需要簡單的工作。 <xref:System.IO.FileAccess.ReadWrite> 是特殊值的範例。  
  
 **X AVOID** 建立旗標列舉，其中某些值的組合會無效。  
  
 **X AVOID** 使用旗標為零的列舉值，除非值代表 「 清除所有旗標 」 且命名為適當的 下一步的指導方針所述。  
  
 **✓ DO** 將零值的旗標列舉 `None`。 對於旗標列舉值必須一律表示 「 清除所有旗標 」。  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a>將值加入至列舉  
 它是很常見發現您需要將值加入至列舉，您有已出貨之後。 沒有潛在的應用程式相容性問題時新增的值會傳回從現有的 API，因為撰寫不夠周全的應用程式可能會正確處理新的值。  
  
 **✓ CONSIDER** 將值加入至忽略小型的相容性風險的列舉。  
  
 如果您有關於列舉的新增項目所造成的應用程式不相容的實際資料，請考慮新增，則傳回新的和舊值的新 API，並取代舊版的 API 應該會繼續傳回舊的值。 這可確保您現有的應用程式保持相容。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [類型設計方針](../../../docs/standard/design-guidelines/type.md)  
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

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
ms.openlocfilehash: 544f617ca3a352814504125d7a61d70db5a81566
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579245"
---
# <a name="enum-design"></a>列舉設計
列舉是特殊類型的實值型別。 有兩種類型的列舉： 簡單列舉和旗標的列舉。  
  
 簡單列舉代表少量已關閉的選項。 簡單列舉的常見範例是一組色彩。  
  
 旗標列舉的設計支援的列舉值的位元運算。 旗標列舉的常見範例是一串選項。  
  
 **✓ DO** 列舉使用強型別參數、 屬性和傳回值，表示一組值。  
  
 **✓ DO** 偏好使用列舉，而不靜態的常數。  
  
 **X DO NOT** 列舉用於開啟設定 （例如作業系統版本、 您的朋友、 等等的名稱。）。  
  
 **X DO NOT** 提供保留的列舉值是要供未來使用。  
  
 您一律只可以在稍後階段，將值加入至現有的列舉。 請參閱[加入值，以列舉](#add_value)如需有關將值加入至列舉。 保留的值只會干擾實際值的集合，而且通常會導致使用者的錯誤。  
  
 **X AVOID** 公開僅有一個值的列舉。  
  
 為確保未來的 C 應用程式開發介面的擴充性常見的作法是將保留的參數加入方法簽章。 這種保留的參數可能會以單一的預設值的列舉。 這不應該在受管理的應用程式開發介面。 方法多載，可新增參數在未來的版本。  
  
 **X DO NOT** sentinel 值包含在列舉中。  
  
 雖然有時候很有幫助 framework 開發人員，sentinel 值會是架構的使用者造成混淆。 它們可用來從列舉所表示的集追蹤狀態的列舉，而不是正在執行其中一個值。  
  
 **✓ DO** 提供簡單列舉上零的值。  
  
 請考慮呼叫值類似"None"。 如果這類值不適合這個特定的列舉，最常見的預設值的列舉應該指派基礎值為零。  
  
 **✓ CONSIDER** 使用 <xref:System.Int32> （大部分的程式設計語言中的預設值） 列舉的基礎類型為除非有下列情況：  
  
-   列舉是旗標列舉，而且您有 32 個以上的旗標，或希望有更多的未來。  
  
-   基礎類型必須是不同於<xref:System.Int32>更容易與預期不同大小列舉的 unmanaged 程式碼的互通性。  
  
-   較小的基礎類型會導致大幅節省空間。 如果您預期的列舉，主要是做為控制流程的引數時，大小會使只有些微的差異。 節省大小可能會很大如果：  
  
    -   您預期要做為經常執行個體化的結構或類別中的欄位列舉。  
  
    -   您預期使用者建立大型陣列或集合的列舉執行個體。  
  
    -   您預期大量列舉来序列化的執行個體。  
  
 對於記憶體使用方式，請留意，受管理的物件都`DWORD`-讓您有效地需要多個列舉或執行個體的總執行個體大小一律是因為，為了有所差別，封裝具有較小的列舉中的其他小結構對齊要無條件進位至`DWORD`。  
  
 **✓ DO** 命名為旗標列舉的複數名詞或名詞片語，並使用單數名詞或名詞片語的簡單列舉。  
  
 **X DO NOT** 擴充 <xref:System.Enum?displayProperty=nameWithType> 直接。  
  
 <xref:System.Enum?displayProperty=nameWithType> 一種特殊類型正由 CLR 建立使用者定義的列舉。 大部分的程式設計語言提供可讓您存取這項功能的程式設計項目。 例如，在 C#`enum`關鍵字用來定義列舉型別。  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a>設計旗標列舉  
 **✓ DO** 套用 <xref:System.FlagsAttribute?displayProperty=nameWithType> 用於旗標列舉。 並不適用此屬性至簡單列舉。  
  
 **✓ DO** 使用的 2 乘冪的旗標列舉值，因此也可以自由地結合使用位元 OR 運算。  
  
 **✓ CONSIDER** 常提供的特殊的列舉值使用的旗標的組合。  
  
 位元運算是一種進階的概念，而且應該不需要簡單的工作。 <xref:System.IO.FileAccess.ReadWrite> 是特殊值的範例。  
  
 **X AVOID** 建立旗標列舉，其中某些值的組合會無效。  
  
 **X AVOID** 使用旗標為零的列舉值，除非值代表 「 清除所有旗標 」 且命名為適當的 下一步的指導方針所述。  
  
 **✓ DO** 將零值的旗標列舉 `None`。 旗標列舉的值必須一律表示 「 清除所有旗標 」。  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a>將值加入至列舉  
 它是很常見發現您需要將值加入至列舉之後您有已出貨。 潛在的應用程式相容性問題時沒有新增的值會傳回從現有的 API，因為撰寫不夠周全的應用程式可能會正確處理新的值。  
  
 **✓ CONSIDER** 將值加入至忽略小型的相容性風險的列舉。  
  
 如果您有關於列舉新增的項目所造成的應用程式不相容的實際資料，請考慮加入新的 API 傳回全新和舊的值，並已被取代的舊的 API，應該會繼續傳回舊的值。 這可確保現有的應用程式保持相容。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [類型設計方針](../../../docs/standard/design-guidelines/type.md)  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

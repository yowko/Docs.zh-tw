---
title: 建構函式設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- default constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ad920c8028b102a13fdfe928d21768538e25b0f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868150"
---
# <a name="constructor-design"></a>建構函式設計
有兩種類型的建構函式： 建構函式和執行個體建構函式的輸入。  
  
 類型建構函式是靜態，而且之前已使用的型別，由 CLR 執行。 建立類型的執行個體時，就會執行執行個體建構函式。  
  
 類型建構函式不能使用任何參數。 可以執行個體建構函式。 不採用任何參數的執行個體建構函式通常稱為 「 預設建構函式。  
  
 建構函式是最自然的方式，來建立型別的執行個體。 大部分的開發人員將搜尋，並嘗試使用建構函式，才能在考慮替代方式來建立執行個體 （例如處理站方法）。  
  
 **✓ CONSIDER** 提供簡單、 在理想情況下預設、 建構函式。  
  
 簡單的建構函式非常少量的參數，而且所有參數都是基本類型或列舉型別。 這類簡單的建構函式會提高使用性的 framework。  
  
 **✓ CONSIDER** 而不建構函式使用的靜態 factory 方法，如果所需的作業語意是否未直接對應至建構的新執行個體，或建構函式設計指導方針並不適合。  
  
 **✓ DO** 以捷徑中使用建構函式參數，設定主要屬性。  
  
 在語意不差異應該能使用空的建構函式後面接著一些屬性集，並使用多個引數的建構函式。  
  
 **✓ DO** 如果建構函式參數用來只設定屬性，使用相同的名稱，建構函式參數和屬性。  
  
 這類參數和屬性之間唯一的差別應該大小寫。  
  
 **✓ DO** 建構函式中的最少工作。  
  
 建構函式應該執行擷取以外的許多工作的建構函式參數。 應該延遲的任何其他的處理成本，直到所需。  
  
 **✓ DO** 擲回例外狀況，從執行個體建構函式，如果適當的話。  
  
 **✓ DO** 明確宣告的公用預設建構函式在類別中，如果需要這類建構函式。  
  
 如果您未明確宣告的型別上的任何建構函式，許多語言 （例如 C# 中) 會自動加入公用預設建構函式。 （抽象類別取得的受保護的建構函式）。  
  
 將參數化建構函式加入至類別，可防止編譯器加入預設建構函式。 這通常會導致意外的重大變更。  
  
 **X AVOID** 明確定義結構的預設建構函式。  
  
 這可讓陣列建立速度更快，因為如果未定義預設建構函式，它不能在陣列中每個位置上執行。 請注意，許多編譯器，包括 C# 中，不允許有基於此原因的無參數建構函式的結構。  
  
 **X AVOID** 其建構函式內的物件上呼叫虛擬成員。  
  
 呼叫虛擬成員會導致最具衍生性的覆寫，以呼叫，即使最具衍生性的類型建構函式已完全尚未執行。  
  
### <a name="type-constructor-guidelines"></a>型別建構函式的指導方針  
 **✓ DO** 私人靜態建構函式。  
  
 靜態建構函式，也稱為類別的建構函式，用來初始化型別。 在建立類型的第一個執行個體，或呼叫該類型上的任何靜態成員之前，CLR 會呼叫靜態建構函式。 使用者已無法控制當呼叫靜態建構函式。 如果靜態建構函式不是私人的它可以由 CLR 以外的程式碼呼叫。 根據建構函式中執行的作業，這可能會導致非預期的行為。 C# 編譯器會強制為私用靜態建構函式。  
  
 **X DO NOT** 擲回例外狀況，從靜態建構函式。  
  
 如果型別建構函式擲回例外狀況，類型不是使用目前的應用程式定義域中。  
  
 **✓ CONSIDER** 初始化的靜態欄位內嵌，而不是使用明確靜態建構函式，因為執行階段能夠使效能最佳化的不需要明確定義的靜態建構函式的類型。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)  
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

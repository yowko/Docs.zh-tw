---
title: "介面設計"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d04011622321638e1f3b0c5f4d270f840c7070e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="interface-design"></a>介面設計
雖然大部分的應用程式開發介面最能模擬使用類別和結構，但是有些的狀況介面比較適合或是唯一的選項。  
  
 CLR 不支援多重繼承 （亦即，CLR 類別不可以繼承自多個基底類別），但它不允許實作除了繼承自基底類別的一個或多個介面的型別。 因此，介面常用來達成的多重繼承的效果。 例如，<xref:System.IDisposable>是一種介面，允許以支援 disposability 它們要加入任何其他繼承階層架構的獨立類型。  
  
 中定義的介面是適當的情況下會建立數種類型，包括一些實值類型必須支援的通用介面。 實值類型無法繼承類型以外<xref:System.ValueType>，但它們可以實作介面，因此使用的介面是唯一的選項，以便提供通用基底型別。  
  
 **✓ 不要**定義介面，如果您需要一組型別，其中包含實值類型必須支援某些一般的 API。  
  
 **✓ 考慮**定義介面，如果您需要在已經繼承自其他類型的型別上支援其功能。  
  
 **請避免 x**使用標記介面 （不含成員的介面）。  
  
 如果您要將類別標示為具有特定特性 （標記），請在一般情況下，使用自訂屬性，而不是介面。  
  
 **✓ 不要**提供至少一個型別是介面的實作。  
  
 此舉有助於驗證介面的設計。 例如，<xref:System.Collections.Generic.List%601>是實作<xref:System.Collections.Generic.IList%601>介面。  
  
 **✓ 不要**提供至少一個應用程式開發介面使用您定義每個介面 （做為參數或屬性取得介面的方法型別為介面）。  
  
 此舉有助於驗證介面設計。 例如，<xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>取用<xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType>介面。  
  
 **X 不**將成員加入至先前已發佈的介面。  
  
 這樣會中斷介面的實作。 您應該建立新的介面，以避免版本控制問題。  
  
 除了這些指導方針所述的情況下，您在一般情況下，應該設計 managed 程式碼可重複使用程式庫選擇類別，而不是介面。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [型別設計指導方針](../../../docs/standard/design-guidelines/type.md)  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

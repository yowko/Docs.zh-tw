---
title: 介面設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
author: KrzysztofCwalina
ms.openlocfilehash: 1f982aa37f92b7270725574d949989ca120297d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026363"
---
# <a name="interface-design"></a>介面設計
雖然大部分 Api 最會使用類別和結構建立模型，但有一些的情況介面比較適合或是唯一的選項。  
  
 CLR 不支援多重繼承 （亦即，CLR 類別無法繼承多個基底類別），但它不允許類型實作一或多個介面，除了繼承自基底類別。 因此，介面常用來達到多重繼承的效果。 比方說，<xref:System.IDisposable>是一種介面，允許以支援 disposability 它們要在其中加入任何其他繼承階層架構的獨立類型。  
  
 在哪一個定義的介面是適當的情況下是建立可由數種類型，包括一些實值型別支援的通用介面。 實值型別無法繼承型別以外<xref:System.ValueType>，但它們可以實作介面，所以使用的介面是唯一的選項，以提供通用的基底類型。  
  
 **✓ DO** 定義介面，如果您需要一組型別，其中包含實值類型必須支援某些一般的 API。  
  
 **✓ CONSIDER** 定義介面，如果您需要在已經繼承自其他類型的型別上支援其功能。  
  
 **X AVOID** 使用標記介面 （不含成員的介面）。  
  
 如果您需要將類別標示為具有特定特性 （標記），在一般情況下，使用自訂屬性，而不是介面。  
  
 **✓ DO** 提供至少一個型別是介面的實作。  
  
 此舉有助於驗證介面的設計。 例如，<xref:System.Collections.Generic.List%601>是實作<xref:System.Collections.Generic.IList%601>介面。  
  
 **✓ DO** 提供至少一個應用程式開發介面使用您定義每個介面 （做為參數或屬性取得介面的方法型別為介面）。  
  
 此舉有助於驗證介面設計。 例如，<xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>耗用<xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType>介面。  
  
 **X DO NOT** 將成員加入至先前已發佈的介面。   
  
 這樣會中斷介面的實作。 您應該建立新的介面，以避免版本控制問題。  
  
 除了這些指導方針所述的情況下，您應，在一般情況下，選擇類別，而不是介面設計的 managed 程式碼可重複使用程式庫。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [類型設計方針](../../../docs/standard/design-guidelines/type.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

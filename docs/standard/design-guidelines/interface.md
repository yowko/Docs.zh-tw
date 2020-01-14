---
title: 介面設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 06b2e0d281314f3bd6346a7dbbd8bb56928fe58b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709292"
---
# <a name="interface-design"></a>介面設計
雖然大部分的 Api 都是使用類別和結構來進行模型化，但有時候介面較合適或是唯一的選項。  
  
 CLR 不支援多重繼承（也就是 CLR 類別無法繼承自一個以上的基類），但是除了繼承自基類之外，它還允許型別執行一或多個介面。 因此，通常會使用介面來達到多重繼承的效果。 例如，<xref:System.IDisposable> 是一個介面，可讓類型支援 disposability，而不受其想要參與的任何其他繼承階層。  
  
 定義介面的另一種情況是建立可由數種類型支援的通用介面，包括一些實數值型別。 實值型別無法繼承自 <xref:System.ValueType>以外的型別，但它們可以實作為介面，因此使用介面是唯一的選項，以便提供一般基底型別。  
  
 如果您需要一些通用 API，以包含實數值型別的一組類型來支援，則**✓**會定義介面。  
  
 如果您需要在已經繼承自其他類型的類型上支援其功能， **✓請考慮**定義介面。  
  
 **X 避免**使用標記介面（沒有成員的介面）。  
  
 如果您需要將類別標示為具有特定特性（標記），則一般會使用自訂屬性，而不是介面。  
  
 **✓確實**提供至少一個型別，也就是介面的執行。  
  
 這麼做有助於驗證介面的設計。 例如，<xref:System.Collections.Generic.List%601> 是 <xref:System.Collections.Generic.IList%601> 介面的執行。  
  
 **✓確實**提供至少一個使用您所定義之介面的 API （此方法會將介面當做參數或屬性輸入為介面）。  
  
 這麼做有助於驗證介面設計。 例如，<xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> 會使用 <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> 介面。  
  
 **X 不會**將成員新增至先前出貨的介面。  
  
 這麼做會中斷介面的實現。 您應該建立新的介面，以避免版本控制問題。  
  
 除了這些指導方針中所述的情況之外，您通常應該選擇 [類別]，而不是 [設計 managed 程式碼可重複使用的程式庫] 中的介面。  
  
 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>請參閱

- [類型設計方針](../../../docs/standard/design-guidelines/type.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

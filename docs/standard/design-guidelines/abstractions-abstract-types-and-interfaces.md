---
title: 抽象 (抽象類型和介面)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ad8b2dd3dbf2a7a75c98a3115d4351dfea4e1a0
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44698356"
---
# <a name="abstractions-abstract-types-and-interfaces"></a>抽象 (抽象類型和介面)
抽象概念是描述合約，但不提供完整的實作合約的型別。 抽象概念通常會實作為抽象類別或介面，和其隨附一組妥善定義的參考文件描述的實作合約的型別所需的語意。 最重要的抽象概念，.NET Framework 中的部分<xref:System.IO.Stream>， <xref:System.Collections.Generic.IEnumerable%601>，和<xref:System.Object>。  
  
 您可以藉由實作具象類型支援抽象類別的合約和 framework Api 取用 （操作） 時，使用此具象型別擴充架構的抽象概念。  
  
 有意義且實用的抽象層能夠承受，測試是時間的很難設計的。 主要的困難取得正確的不多也不較少的成員集。 如果抽象概念會有太多的成員，會變得很困難或甚至根本不可能實作。 如果有太少的成員，承諾的功能，它會變成在許多有趣的案例。  
  
 太多的抽象概念的架構中也有負面影響使用性的 framework。 它通常是很難了解抽象概念，而不需要了解它如何融入相通的具象實作，運作於抽象概念的 Api。 此外，抽象概念和其成員的名稱是抽象的這樣會使得它們都使用加密和親近而不需要先了解其使用方式的更廣泛的內容。  
  
 不過，抽象概念會提供功能極為強大的擴充性，通常無法比對的其他擴充性機制。 也就是核心的許多架構模式的詳細資訊，例如外掛程式，逆轉控制 (IoC)、 管線等等。 它們也是非常重要的可測試性的架構。 良好的抽象概念可使您能夠建立單元測試以大量相依性。 總而言之，抽象化是負責大快人心的豐富功能的現代的物件導向架構。  
  
 **X DO NOT** 提供抽象，除非它們經過開發數種具象實作和應用程式開發介面使用的抽象概念。  
  
 **✓ DO** 設計抽象時請小心選擇之間的抽象類別和介面。  
  
 **✓ CONSIDER** 提供參考測試的具象實作的抽象概念。 這類測試應該允許使用者來測試是否正確實作它們的實作的合約。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
- [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)

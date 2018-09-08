---
title: 虛擬成員
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92b648e7886fb0214238e32eacae2870b470340
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193571"
---
# <a name="virtual-members"></a>虛擬成員
虛擬成員可以被覆寫，因此變更子類別的行為。 它們是回呼提供，擴充性方面相當類似，但它們會有較高的執行效能和記憶體耗用量。 此外，虛擬成員覺得在需要建立一種特殊種類的現有類型 （特製化） 的情況下更自然的。  
  
 虛擬成員會優於回呼和事件，但不是會被執行優於非虛擬方法。  
  
 虛擬成員的主要缺點是只可以在編譯時修改虛擬成員的行為。 回呼的行為可以在執行階段修改。  
  
 虛擬成員，例如回呼 （和可能有多個回呼），是設計、 測試及維護，因為虛擬成員的任何呼叫可以覆寫非預期的方式，而且可以執行任意程式碼的成本。 此外，更多精力通常需要清楚定義的虛擬成員的合約，讓設計與記錄它們的成本較高。  
  
 **X DO NOT** 讓成員虛擬，除非您有很好的理由，若要這樣做，而且您了解所有設計、 測試及維護虛擬成員與相關的成本。  
  
 虛擬成員會較少能夠容許方面可以對它們而不會中斷相容性的變更。 此外，也就是低於非虛擬成員，這多半是因為呼叫虛擬成員不會內嵌。  
  
 **✓ CONSIDER** 限制只是絕對必要的擴充性。  
  
 **✓ DO** 不用公用存取範圍中的受保護的存取範圍，在虛擬成員。 Public 成員應該提供擴充性 （如有必要） 藉由呼叫受保護的虛擬成員。  
  
 類別的 public 成員應該為該類別的直接取用者提供正確的功能集。 虛擬成員設計用來覆寫子類別，在和受保護的存取範圍是範圍可以要使用的所有虛擬擴充性點的好方法。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
- [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)

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
ms.openlocfilehash: fa4227fc4476b86f07216650b22fccc25af7dd98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573083"
---
# <a name="virtual-members"></a>虛擬成員
虛擬成員會覆寫，因此變更子類別的行為。 它們是回呼提供，擴充性方面相當類似，但是可以執行效能和記憶體耗用量方面更好。 此外，虛擬成員感覺更自然的案例中，需要建立一個特殊種類的現有類型 （特製化）。  
  
 虛擬成員的執行效能優於回撥和事件，但不是執行效能優於非虛擬方法。  
  
 虛擬成員的主要缺點是虛擬成員的行為只發生在編譯階段中變更。 回呼的行為可以在執行階段修改。  
  
 虛擬成員，例如回呼，可能有多個回呼成本很高設計、 測試和維護，因為任何呼叫虛擬成員會覆寫非預期的方式，而且可以執行任意程式碼。 此外，還要更多的投入時間通常才能清楚地定義合約的虛擬成員，讓設計和撰寫它們的成本較高者為。  
  
 **X DO NOT**讓成員虛擬，除非您有很好的理由，若要這樣做，而且您了解所有設計、 測試及維護虛擬成員與相關的成本。  
  
 虛擬成員都是較少能夠容許方面可能會對它們而不會中斷相容性的變更。 此外，它們不低於非虛擬的成員，主要是因為不是內嵌的虛擬成員的呼叫。  
  
 **✓ CONSIDER**限制只是絕對必要的擴充性。  
  
 **✓ DO**不用公用存取範圍中的受保護的存取範圍，在虛擬成員。 Public 成員應該提供擴充性 （如有必要） 藉由呼叫受保護的虛擬成員。  
  
 類別的 public 成員應該提供正確的功能集，該類別的直接取用者。 虛擬成員設計用來覆寫中的子類別，以及受保護的存取範圍是領域可以要使用的所有虛擬擴充性點的好方法。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)

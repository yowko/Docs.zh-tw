---
title: Protected 成員
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: 14ef02a760c9d4b77fe058334baffd63fcf29cfd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709097"
---
# <a name="protected-members"></a>Protected 成員
受保護成員本身並不提供任何擴充性，但可以透過子類別化更強大的方式進行擴充性。 它們可用來公開先進的自訂選項，而不會不必要地使主要公用介面複雜化。  
  
 架構設計人員必須謹慎使用受保護的成員，因為「受保護」的名稱可能會提供不安全的安全性意義。 任何人都可以將未密封的類別子類別化，並存取受保護的成員，因此，公用成員所使用的所有相同的防禦性編碼做法都適用于受保護的成員。  
  
 **✓請考慮**使用受保護的成員進行 advanced 自訂。  
  
 **✓**會將未密封類別中的受保護成員視為公用，以做為安全性、檔和相容性分析的目的。  
  
 任何人都可以繼承自類別，並存取受保護的成員。  
  
 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)

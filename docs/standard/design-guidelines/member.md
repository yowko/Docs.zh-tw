---
title: 成員設計方針
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
ms.openlocfilehash: cf4f1d2fee73e3e65dc4d92ea97a62f4a7e4c4e5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709266"
---
# <a name="member-design-guidelines"></a>成員設計方針
方法、屬性、事件、函數和欄位統稱為成員。 成員最終是對架構的使用者公開架構功能的方式。  
  
 成員可以是 virtual 或非虛擬、具體或抽象、靜態或實例，而且可以有數個不同的存取範圍。 這一切都能提供驚人的表達，但同時需要特別注意架構設計工具的一部分。  
  
 本章提供在設計任何類型的成員時應遵循的基本方針。  
  
## <a name="in-this-section"></a>本章節內容  
 [成員多載](../../../docs/standard/design-guidelines/member-overloading.md)  
 [屬性設計](../../../docs/standard/design-guidelines/property.md)  
 [建構函式設計](../../../docs/standard/design-guidelines/constructor.md)  
 [事件設計](../../../docs/standard/design-guidelines/event.md)  
 [欄位設計](../../../docs/standard/design-guidelines/field.md)  
 [擴充方法](../../../docs/standard/design-guidelines/extension-methods.md)  
 [運算子多載](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [參數設計](../../../docs/standard/design-guidelines/parameter-design.md)  
 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

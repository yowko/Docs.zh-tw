---
title: 擴充性設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: cd5db2d1e299df1b3d0f706ebc507e6855b72505
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709461"
---
# <a name="designing-for-extensibility"></a>擴充性設計
設計架構的其中一個重要層面，就是確定已仔細考慮架構的擴充性。 這需要您瞭解與各種擴充性機制相關聯的成本和優點。 這一章可協助您決定哪些擴充性機制（子類別、事件、虛擬成員、回呼等等）最符合您的架構需求。  
  
 有許多方法可讓您在架構中提供擴充性。 其範圍從較不強大，但成本較低，但成本低廉。 針對任何指定的擴充性需求，您應該選擇符合需求的成本最低的擴充性機制。 請記住，稍後可能會加入更多擴充性，但您永遠不會在不引入重大變更的情況下將它移開。  
  
## <a name="in-this-section"></a>本章節內容  
 [非密封類別](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [Protected 成員](../../../docs/standard/design-guidelines/protected-members.md)  
 [事件和回呼](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [虛擬成員](../../../docs/standard/design-guidelines/virtual-members.md)  
 [抽象 (抽象類型和介面)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [實作抽象的基底類別](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [密封](../../../docs/standard/design-guidelines/sealing.md)  
 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

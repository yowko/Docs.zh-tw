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
ms.openlocfilehash: 406c15b6ce42b637ed1bbb61761d05e040995579
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280240"
---
# <a name="designing-for-extensibility"></a>擴充性設計
設計架構的其中一個重要層面，就是確定已仔細考慮架構的擴充性。 這需要您瞭解與各種擴充性機制相關聯的成本和優點。 這一章可協助您決定哪些擴充性機制（子類別、事件、虛擬成員、回呼等等）最符合您的架構需求。  
  
 有許多方法可讓您在架構中提供擴充性。 其範圍從較不強大，但成本較低，但成本低廉。 針對任何指定的擴充性需求，您應該選擇符合需求的成本最低的擴充性機制。 請記住，稍後可能會加入更多擴充性，但您永遠不會在不引入重大變更的情況下將它移開。  
  
## <a name="in-this-section"></a>本節內容  
 [未密封的類別](unsealed-classes.md)  
 [受保護的成員](protected-members.md)  
 [事件和回呼](events-and-callbacks.md)  
 [虛擬成員](virtual-members.md)  
 [抽象（抽象類別型和介面）](abstractions-abstract-types-and-interfaces.md)  
 [用來執行抽象概念的基類](base-classes-for-implementing-abstractions.md)  
 [密封](sealing.md)  
 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**  
  
## <a name="see-also"></a>另請參閱

- [架構設計方針](index.md)

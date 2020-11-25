---
title: 擴充性設計
ms.date: 10/22/2008
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: 7b7b1bcfc907612be12e7f8ca7114183f7e830ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734448"
---
# <a name="designing-for-extensibility"></a>擴充性設計

設計架構的其中一個重要層面，是確定已謹慎考慮架構的擴充性。 這需要您瞭解與各種擴充性機制相關聯的成本與優點。 本章可協助您決定哪一個擴充性機制（子類別化、事件、虛擬成員、回呼等等）最符合您的架構需求。  
  
 有許多方式可讓您在架構中進行擴充。 其範圍從較不強大，但是成本較低，但成本較高，但成本較高。 針對任何指定的擴充性需求，您應該選擇符合需求的成本最低的擴充性機制。 請記住，您通常可以稍後再加入更多的擴充性，但您永遠不需要再帶出重大變更。  
  
## <a name="in-this-section"></a>本節內容  

 [未密封的類別](unsealed-classes.md)  
 [受保護的成員](protected-members.md)  
 [事件和回呼](events-and-callbacks.md)  
 [虛擬成員](virtual-members.md)  
 [抽象型別和介面 (抽象類別) ](abstractions-abstract-types-and-interfaces.md)  
 [用來執行抽象概念的基類](base-classes-for-implementing-abstractions.md)  
 [密封](sealing.md)  
 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [架構設計指導方針](index.md)

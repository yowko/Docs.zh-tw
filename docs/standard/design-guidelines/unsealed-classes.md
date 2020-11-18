---
title: 非密封類別
ms.date: 10/22/2008
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: b2e14b435aa567f231230da34307014210d46ccb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828513"
---
# <a name="unsealed-classes"></a>非密封類別
密封類別不能繼承自，而且它們會防止擴充性。 相反地，可繼承的類別稱為未密封類別。

 ✔️考慮使用未密封的類別，而不是加入虛擬或受保護的成員，這是為架構提供便宜的擴充性的絕佳方法。

 開發人員通常會想要繼承自未密封的類別，以便加入方便的成員，例如自訂的函式、新方法或方法多載。 例如，  `System.Messaging.MessageQueue` 未密封，因此可讓使用者建立預設為特定佇列路徑的自訂佇列，或新增自訂方法，以簡化特定案例的 API。

 在大部分的程式設計語言中，類別預設是未密封的，而且在架構中，大部分的類別也是建議的預設值。 非密封型別所提供的擴充性，是由架構使用者所提供，且相當便宜，因為與非密封類型相關聯的測試成本相對較低。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [架構設計指導方針](index.md)
- [擴充性設計](designing-for-extensibility.md)
- [密封](sealing.md)

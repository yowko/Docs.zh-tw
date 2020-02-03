---
title: 非密封類別
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 6804a79e8beee1d42e313509966b46239e66c25f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743559"
---
# <a name="unsealed-classes"></a>非密封類別
密封類別無法繼承自，而且它們會阻止擴充性。 相反地，可以繼承自的類別稱為未密封的類別。

 ✔️考慮使用未密封的類別，而不加入虛擬或受保護的成員，以提供價格實惠但對架構的擴充性的絕佳方法。

 開發人員通常會想要從未密封的類別繼承，以便加入方便的成員，例如自訂的函數、新方法或方法多載。 例如，`System.Messaging.MessageQueue` 未密封，因此可讓使用者建立預設為特定佇列路徑的自訂佇列，或新增自訂方法來簡化特定案例的 API。

 在大部分的程式設計語言中，類別預設為未密封，在架構中，大部分的類別也是建議使用的預設值。 非密封類型所提供的擴充性非常感謝架構使用者，而且因為與非密封類型相關聯的測試成本相對較低，所以不太需要這麼做。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition[ 節錄。](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)*

## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [密封](../../../docs/standard/design-guidelines/sealing.md)

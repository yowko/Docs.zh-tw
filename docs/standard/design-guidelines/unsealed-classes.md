---
title: 非密封類別
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: KrzysztofCwalina
ms.openlocfilehash: d7174de7ddf062b829672e04952c1010fcb74058
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778790"
---
# <a name="unsealed-classes"></a>非密封類別
密封的類別無法被繼承，並循環讓擴充性。 相反地，可以繼承自的類別稱為未密封的類別。  
  
 **✓ CONSIDER** 沒有使用未密封的類別新增虛擬或受保護成員，為提供低成本的好方法卻高價值為架構的擴充性。  
  
 開發人員通常會想要繼承自未密封的類別，以便加入方便的成員，例如自訂建構函式、 新的方法或方法多載。 比方說，`System.Messaging.MessageQueue`未密封，因此可讓使用者建立自訂的佇列預設為特定的佇列路徑，或加入自訂的方法，可簡化針對特定案例的 API。  
  
 根據預設，在多數程式設計語言中，未密封的類別是，這也是在架構中的大部分類別的建議預設值。 非密封類型所提供的擴充性是更令人激賞的 framework 使用者，因為非密封類型相關聯的相對較低的測試成本提供成本很低。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [密封](../../../docs/standard/design-guidelines/sealing.md)

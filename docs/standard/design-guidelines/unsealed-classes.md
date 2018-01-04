---
title: "非密封類別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ec66fb3dea74e6f738ec308ce0f88945526a0a77
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="unsealed-classes"></a>非密封類別
密封的類別無法被繼承，以及它們會防止擴充性。 相反地，可以繼承自的類別稱為未密封的類別。  
  
 **✓ 考慮**沒有使用未密封的類別新增虛擬或受保護成員，為提供低成本的好方法卻高價值為架構的擴充性。  
  
 開發人員通常會想要繼承自非密封類別，以新增方便成員，例如自訂建構函式、 新的方法或方法多載。 例如，`System.Messaging.MessageQueue`未密封，因此可讓使用者建立自訂的佇列的特定佇列路徑的預設或加入自訂方法，可簡化針對特定案例的 API。  
  
 根據預設，在最具備程式設計語言中，未密封的類別是，這也是建議的預設值為架構中，大部分的類別。 非密封類型所提供的擴充性是由 framework 使用者很令人激賞和相當耗費大量資源因為相對較低的測試與未密封的型別相關聯的成本提供。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [密封](../../../docs/standard/design-guidelines/sealing.md)

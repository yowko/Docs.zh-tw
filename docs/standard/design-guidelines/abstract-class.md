---
title: 抽象類別設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5b9dacc4995a126e1ee3f6062dca796194d4882
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178623"
---
# <a name="abstract-class-design"></a>抽象類別設計
**X DO NOT** 抽象型別中定義公用或受保護的內部建構函式。  
  
 建構函式應該是公用，只有當使用者將需要建立型別的執行個體。 因為您無法建立抽象類型的執行個體，具有公用建構函式的抽象類型是不正確設計，且可能造成誤導使用者。  
  
 **✓ DO** 抽象類別中定義受保護或內部的建構函式。  
  
 受保護的建構函式是更常見的並只允許基底類別，以建立子型別時進行自己的初始化。  
  
 內部的建構函式可用來限制要定義類別的組件的抽象類別的具象實作。  
  
 **✓ DO** 提供至少一個繼承自每個您寄送的抽象類別的具象型別。  
  
 此舉有助於驗證抽象類別的設計。 例如，<xref:System.IO.FileStream?displayProperty=nameWithType>是實作<xref:System.IO.Stream?displayProperty=nameWithType>抽象類別。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [類型設計方針](../../../docs/standard/design-guidelines/type.md)  
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

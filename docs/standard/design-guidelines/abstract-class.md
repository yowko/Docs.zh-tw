---
title: 抽象類別設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
author: KrzysztofCwalina
ms.openlocfilehash: 6eec3bb4575b89c6476e6c3410050c705141777f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550407"
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
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [類型設計方針](../../../docs/standard/design-guidelines/type.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

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
ms.openlocfilehash: 28052cc6848d77acbdf8e9381146ca6fb06c15d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="abstract-class-design"></a>抽象類別設計
**X 不**抽象型別中定義公用或受保護的內部建構函式。  
  
 應該只有當使用者將需要建立類型的執行個體的公用建構函式。 因為您無法建立抽象類型的執行個體，具有公用建構函式的抽象類型是不正確地設計與誤導使用者。  
  
 **✓ 不要**抽象類別中定義受保護或內部的建構函式。  
  
 受保護的建構函式更常見，並只允許基底類別建立子型別時執行它自己的初始化。  
  
 內部的建構函式可以用來限制要定義類別的組件的抽象類別的具象實作。  
  
 **✓ 不要**提供至少一個繼承自每個您寄送的抽象類別的具象型別。  
  
 此舉有助於驗證抽象類別的設計。 例如，<xref:System.IO.FileStream?displayProperty=nameWithType>是實作<xref:System.IO.Stream?displayProperty=nameWithType>抽象類別。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [類型設計方針](../../../docs/standard/design-guidelines/type.md)  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

---
title: "Protected 成員"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c3aacd0f08641c01200f0b1791a78413a306590
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="protected-members"></a>Protected 成員
受保護的成員，本身不提供任何擴充性，但會讓透過子類別化的擴充性功能更強大。 它們可以用於不含不必要地複雜的主要公用介面公開進階的自訂選項。  
  
 架構設計人員必須謹慎使用受保護成員因為 「 受保護 」 的名稱可以提供感應的安全性。 任何人都可以子類別的未密封類別，然後存取受保護成員，用於公用成員的防衛性程式碼撰寫方式完全相同，套用至受保護的成員。  
  
 **✓ 考慮**使用受保護的進階自訂的成員。  
  
 **✓ 不要**為用於安全性、 文件，以及相容性的分析公用非密封類別以處理受保護的成員。  
  
 任何人都可以繼承自類別，並存取受保護的成員。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)

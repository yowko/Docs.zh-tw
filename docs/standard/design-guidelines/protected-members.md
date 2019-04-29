---
title: Protected 成員
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
author: KrzysztofCwalina
ms.openlocfilehash: 7d940f10799df2efc6c6d031781e1ef7cf777dd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937393"
---
# <a name="protected-members"></a>Protected 成員
受保護的成員，本身不提供任何擴充性，但它們可以讓透過子類別化的擴充性功能更強大。 它們可以用來公開 （expose） 而不需要不必要地複雜的主要公用介面的進階的自訂選項。  
  
 架構設計人員必須謹慎使用受保護的成員，是因為 「 受保護 」 的名稱可以讓安全性的錯覺。 任何人都能夠子類別的未密封的類別，然後存取受保護成員，因此相同的所有用於公用成員的防禦性程式碼撰寫慣例套用至受保護的成員。  
  
 **✓ CONSIDER** 使用受保護的進階自訂的成員。  
  
 **✓ DO** 為用於安全性、 文件，以及相容性的分析公用非密封類別以處理受保護的成員。  
  
 任何人都可以繼承自的類別，並存取受保護的成員。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)

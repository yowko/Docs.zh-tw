---
title: 命名資源
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
author: KrzysztofCwalina
ms.openlocfilehash: 5331c82069bb289c282e746841f5a328e2e628f2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130865"
---
# <a name="naming-resources"></a>命名資源
因為可以透過特定的物件參考可當地語系化的資源，如同它們是屬性，就有一個資源的命名方針如下屬性指導方針。  
  
 **✓ DO** PascalCasing 用於資源索引鍵。  
  
 **✓ DO** 提供描述性的而不是簡短的識別項。  
  
 **X DO NOT** 使用主要的 CLR 語言的語言特有的關鍵字。  
  
 **✓ DO** 使用只使用英數字元和底線命名資源。  
  
 **✓ DO** 下列命名慣例用於例外狀況訊息的資源。  
  
 例外狀況型別名稱再加上例外狀況的簡短識別項，應該使用的資源識別碼：  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
- [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)

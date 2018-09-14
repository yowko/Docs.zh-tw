---
title: 命名資源
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5b53fc383e6fc9a5f056bab4eabde9979cd734b
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45507963"
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
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
- [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)

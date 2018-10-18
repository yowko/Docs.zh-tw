---
title: 命名參數
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e6a8a1dcdcb8fa3311b040c72987f0f76e681fc
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086468"
---
# <a name="naming-parameters"></a>命名參數
除了可讀性的明顯原因，請務必遵循的指導方針的參數名稱，因為參數會顯示在文件，並在設計工具中，視覺化設計工具提供 Intellisense 和瀏覽功能的類別時。  
  
 **✓ DO** 將 camelCasing 用於參數名稱。  
  
 **✓ DO** 使用描述性的參數名稱。  
  
 **✓ CONSIDER** 使用根據參數的意義，而不是參數的型別名稱。  
  
### <a name="naming-operator-overload-parameters"></a>運算子多載參數命名  
 **✓ DO** 使用 `left` 和 `right` 的二元運算子多載參數名稱是否有任何參數的意義。  
  
 **✓ DO** 使用 `value` 的一元運算子多載的參數名稱是否有任何參數的意義。  
  
 **✓ CONSIDER** 有意義的名稱，如運算子多載參數，如果這樣做會增加重要的值。  
  
 **X DO NOT** 使用縮寫或數值索引運算子多載的參數名稱。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
- [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)

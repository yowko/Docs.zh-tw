---
title: 命名參數
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 0bb67056bb39b6a5f372191a1d0b0bb0dc1fe4d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709175"
---
# <a name="naming-parameters"></a>命名參數
除了可讀性的明顯原因之外，請務必遵循參數名稱的指導方針，因為當視覺化設計工具提供 Intellisense 和類別流覽功能時，參數會顯示在檔和設計師中。  
  
 **✓ DO**在參數名稱中使用 camelCasing。  
  
 **✓ DO**使用描述性參數名稱。  
  
 **✓請考慮**根據參數的意義（而非參數的類型）來使用名稱。  
  
### <a name="naming-operator-overload-parameters"></a>命名運算子多載參數  
 如果參數沒有意義， **✓**會使用 `left`，並 `right` 二元運算子多載參數名稱。  
  
 如果參數沒有意義，則**✓**會使用一元運算子多載參數名稱 `value`。  
  
 如果這樣做會增加重要的值，✓會針對運算子多載參數**考慮**有意義的名稱。  
  
 **X 不會**針對運算子多載參數名稱使用縮寫或數值索引。  
  
 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)

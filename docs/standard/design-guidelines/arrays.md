---
title: 陣列
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ac7e28c3172f2ed68d402e1d04a1664644c7f25
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2018
ms.locfileid: "45658714"
---
# <a name="arrays"></a>陣列
**✓ DO** 偏好使用透過公用應用程式開發介面中的陣列的集合。 [集合](../../../docs/standard/design-guidelines/guidelines-for-collections.md)節提供有關如何選擇集合和陣列的詳細資料。  
  
 **X DO NOT** 使用唯讀陣列欄位。 欄位本身是唯讀的而且無法變更，但是可以變更陣列中的項目。  
  
 **✓ CONSIDER** 使用不規則的陣列，而不要使用多維度陣列。  
  
 不規則的陣列是也是陣列的元素的陣列。 產生的項目陣列可以是不同的大小，導致相較於多維陣列的某些資料集的資料 （例如，疏鬆矩陣） 較不會浪費空間。 此外，CLR 最佳化不規則的陣列索引作業，因此它們可能會表現出更好的執行階段效能，在某些情況下。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Array>  
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
- [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)

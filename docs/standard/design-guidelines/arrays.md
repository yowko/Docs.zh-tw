---
title: 陣列
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
author: KrzysztofCwalina
ms.openlocfilehash: dd30cdee0440553a9f955f0b3f4ee420e938b9ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864113"
---
# <a name="arrays"></a>陣列
**✓ DO** 偏好使用透過公用應用程式開發介面中的陣列的集合。 [集合](../../../docs/standard/design-guidelines/guidelines-for-collections.md)節提供有關如何選擇集合和陣列的詳細資料。  
  
 **X DO NOT** 使用唯讀陣列欄位。 欄位本身是唯讀的而且無法變更，但是可以變更陣列中的項目。  
  
 **✓ CONSIDER** 使用不規則的陣列，而不要使用多維度陣列。  
  
 不規則的陣列是也是陣列的元素的陣列。 產生的項目陣列可以是不同的大小，導致相較於多維陣列的某些資料集的資料 （例如，疏鬆矩陣） 較不會浪費空間。 此外，CLR 最佳化不規則的陣列索引作業，因此它們可能會表現出更好的執行階段效能，在某些情況下。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Array>
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)

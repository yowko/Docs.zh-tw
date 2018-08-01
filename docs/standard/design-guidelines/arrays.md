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
ms.openlocfilehash: 2945ead7c22b759ce88f6585e2254e9bc540a7ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570391"
---
# <a name="arrays"></a>陣列
**✓ DO**偏好使用透過公用應用程式開發介面中的陣列的集合。 [集合](../../../docs/standard/design-guidelines/guidelines-for-collections.md)> 一節提供有關如何選擇集合和陣列的詳細資料。  
  
 **X DO NOT**使用唯讀陣列欄位。 欄位為唯讀且無法變更，但是可以變更在陣列中的項目。  
  
 **✓ CONSIDER**使用不規則的陣列，而不要使用多維度陣列。  
  
 不規則的陣列是也是陣列的元素的陣列。 組成元素的陣列可以是不同的大小，相較於多維陣列的某些資料 （例如疏鬆矩陣） 集而言較不浪費空間。 此外，CLR 最佳化不規則的陣列索引作業，讓它們可能會出現在某些情況下更好的執行階段效能。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Array>  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)

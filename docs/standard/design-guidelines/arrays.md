---
title: 陣列
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: d4a1f379a88231654c710b1df7b505316377c915
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741800"
---
# <a name="arrays"></a>陣列
✔️偏好在公用 Api 中使用陣列的集合。 [[集合](../../../docs/standard/design-guidelines/guidelines-for-collections.md)] 區段提供如何在集合和陣列之間進行選擇的詳細資料。

 ❌ 不要使用唯讀陣列欄位。 欄位本身是唯讀的，而且無法變更，但陣列中的元素可以變更。

 ✔️考慮使用不規則陣列，而不是多維度陣列。

 不規則陣列是一種陣列，其中包含同時也是陣列的元素。 組成元素的陣列可以是不同的大小，因此，某些資料集（例如，疏鬆陣列）相較于多維度陣列，會浪費更少的空間。 此外，CLR 會優化不規則陣列上的索引作業，因此在某些情況下可能會表現出更佳的執行時間效能。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition[ 節錄。](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)*

## <a name="see-also"></a>另請參閱

- <xref:System.Array>
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)

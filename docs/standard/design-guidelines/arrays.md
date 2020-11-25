---
title: 陣列
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: 11c1d23af4cf599ba632144634947520a1647ae7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701389"
---
# <a name="arrays"></a>陣列

✔️想要在公用 Api 中使用集合，而不是陣列。 [ [集合](guidelines-for-collections.md) ] 區段提供如何在集合和陣列之間進行選擇的詳細資料。

 ❌ 請勿使用唯讀陣列欄位。 欄位本身是唯讀的，而且無法變更，但陣列中的元素可以變更。

 ✔️考慮使用不規則陣列，而不是多維陣列。

 不規則陣列是陣列，其元素也是陣列。 組成專案的陣列可以是不同的大小，導致某些資料集的空間浪費較少， (例如，相較于多維陣列，疏鬆陣列) 。 此外，CLR 會將不規則陣列的索引作業優化，因此在某些情況下，它們可能會表現出更好的執行時間效能。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>另請參閱

- <xref:System.Array>
- [架構設計指導方針](index.md)
- [使用指導方針](usage-guidelines.md)

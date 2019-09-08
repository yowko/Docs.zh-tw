---
title: Null 語意
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: d0b18c0a699840d11f5e4add05147672f9bb69e9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792975"
---
# <a name="null-semantics"></a>Null 語意
下表提供[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]檔的各部分連結，其中`null`會討論（`Nothing`在 Visual Basic）問題。  
  
|主題|描述|  
|-----------|-----------------|  
|[SQL-CLR 類型不符](sql-clr-type-mismatches.md)|本主題的「Null 語義」一節包含三個狀態的 SQL 布林值與雙狀態 common language runtime <xref:System.Boolean>（CLR）、常`Nothing`值（Visual Basic）和`null` （C#）以及其他類似的討論發出.|  
|[標準查詢運算子轉譯](standard-query-operator-translation.md)|本主題的「Null 語意」一節描述 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]中的 null 比較語意。|  
|[System.String 方法](system-string-methods.md)|本主題的「與 .NET 的差異」一節描述 <xref:System.String.LastIndexOf%2A> 傳回 0 即表示字串為 null 或找到的位置為 0 的原因。|  
|[計算數值序列中各值的總和](compute-the-sum-of-values-in-a-numeric-sequence.md)|描述<xref:System.Linq.Enumerable.Sum%2A>運算子如何針對只包含 null`Nothing`的序列或空的序列，評估為（在 Visual Basic 中）， `null`而不是0。|  
  
## <a name="see-also"></a>另請參閱

- [資料類型和函式](data-types-and-functions.md)

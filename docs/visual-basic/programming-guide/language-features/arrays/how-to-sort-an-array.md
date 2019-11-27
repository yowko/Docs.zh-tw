---
title: 如何：排序陣列
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 3fb9af8de0fc86075fdccd64506c855c1c720660
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351845"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>如何：在 Visual Basic 中排序陣列

本文說明如何在 Visual Basic 中排序字串陣列的範例。

## <a name="example"></a>範例

這個範例會宣告名為 `zooAnimals`的 `String` 物件陣列，填入它，然後依字母順序排序：
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a>穩固程式設計

以下條件可能會造成例外狀況：

- 陣列是空的（<xref:System.ArgumentNullException> 類別）。
- Array 是多維度（<xref:System.RankException> 類別）。
- 陣列的一或多個元素不會執行 <xref:System.IComparable> 介面（<xref:System.InvalidOperationException> 類別）。

## <a name="see-also"></a>請參閱

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [陣列](index.md)
- [陣列的疑難排解](troubleshooting-arrays.md)
- [集合](../../concepts/collections.md)
- [For Each...Next 陳述式](../../../language-reference/statements/for-each-next-statement.md)

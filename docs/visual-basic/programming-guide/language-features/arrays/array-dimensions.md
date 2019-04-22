---
title: Array Dimensions in Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: 0b4e7c9e253f94e1e28700c8669d28799ab69d91
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836931"
---
# <a name="array-dimensions-in-visual-basic"></a>Array Dimensions in Visual Basic
A*維度*是在其中您可以變更陣列的項目規格的方向。 保留每一天的月份的銷售總額的陣列有一個維度 （月份天數）。 保留每一天的月份部門銷售總額的陣列具有兩個維度 （的部門編號及月份天數）。 陣列的維度數目會呼叫其*陣序規範*。  
  
> [!NOTE]
>  您可以使用<xref:System.Array.Rank%2A>屬性來判斷陣列中有多少維度。  
  
## <a name="working-with-dimensions"></a>使用的維度  
 您藉由提供指定的陣列項目*index*或*註標*針對其每一個維度。 項目是依據每個維度從索引 0 到最高的索引，該維度的連續項目。  
  
 下圖顯示概念性結構的陣列順位不同。 在圖例中的每個項目會顯示存取它的索引值。 例如，您可以存取的二維陣列中的第二個資料列的第一個項目指定的索引`(1, 0)`。  
  
 ![此圖顯示的一維陣列。](./media/array-dimensions/one-dimensional-array.gif)  
  
 ![此圖顯示的二維陣列。](./media/array-dimensions/two-dimensional-array.gif)  
  
 ![此圖顯示一個三維陣列。](./media/array-dimensions/three-dimensional-array.gif)  
  
### <a name="one-dimension"></a>一維  
 許多陣列有只有一個維度，例如每個年齡的人的數目。 將項目指定唯一的需求是該元素保留計數的年齡。 因此，這類陣列會使用一個索引。 下列範例宣告的變數來保存*的一維陣列*的時代中，計算歲到 120 之間的 0。  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a>兩個維度  
 某些陣列有兩個維度，例如每個樓層的校園每棟建築物的辦公室的數目。 規格的項目需要的建築物號碼與最低限度值，而每個元素會保留該組合的建築物和樓層的計數。 因此，這類陣列會使用兩個索引。 下列範例宣告的變數來保存*二維陣列*office 計數，0 到 40 的建築物和樓層 0 到 5。  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 二維陣列，也會呼叫*矩形陣列*。  
  
### <a name="three-dimensions"></a>三個維度  
 少數的陣列有三個維度，例如在 3d 空間中的值。 這類陣列會使用在此情況下代表 x、 y 和 z 座標的實體空間中的三個索引。 下列範例宣告的變數來保存*三維陣列*的三維的磁碟區在各個點上的無線溫度。  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a>三個以上的維度  
 雖然陣列可以有多達 32 個維度，很少會有三個以上。  
  
> [!NOTE]
>  當您將維度加入陣列時，陣列所需的儲存體總計會增加相當大，因此請謹慎使用多維陣列。  
  
## <a name="using-different-dimensions"></a>使用不同的維度  
 假設您想要追蹤的存在的每月每一天的銷售金額。 您可以宣告一維陣列 31 項目時，其中每一天的月份，如下列範例會顯示。  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 現在假設您想要追蹤的相同資訊不只會針對每一天的每個月，也包含一年的每個月。 您可以宣告 （如月份） 12 個資料列與 （適用於天），31 個資料行的二維陣列，如下列範例所示。  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 現在假設您決定要讓您的陣列就會保留一年以上的資訊。 如果您想要追蹤 5 年的銷售金額，您可以宣告一個三維陣列 5 個層級、 12 個資料列中，與 31 個資料行，如下列範例所示。  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 請注意，因為每個索引從 0 會變化，其最大值，每個維度的`salesAmounts`宣告為所需的長度小於該維度。 也請注意，陣列的大小會增加每個新的維度。 在上述範例中的三種大小分別為 31、 372 和 1860 個元素。  
  
> [!NOTE]
>  您可以建立陣列，而不使用`Dim`陳述式或`New`子句。 例如，您可以呼叫<xref:System.Array.CreateInstance%2A>方法或另一個元件可以通過您的程式碼以這種方式建立的陣列。 這類陣列可以有 0 以外的下限。 您可以一律測試作為維度的下限，利用<xref:System.Array.GetLowerBound%2A>方法或`LBound`函式。  
  
## <a name="see-also"></a>另請參閱

- [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [陣列的疑難排解](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)

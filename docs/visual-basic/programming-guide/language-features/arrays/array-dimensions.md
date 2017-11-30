---
title: Array Dimensions in Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21e170ca5942862a26e05428fffaea7d1e875e19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="array-dimensions-in-visual-basic"></a>Array Dimensions in Visual Basic
A*維度*是的方向，在其中您可以不同的陣列項目的規格。 保留每一天的月份的銷售總額陣列都有一個維度 （月份的天數）。 保留每個月份的天數部門銷售總額的陣列具有兩個維度 （的部門編號及月份天數）。 陣列的維度的數目會呼叫其*陣序規範*。  
  
> [!NOTE]
>  您可以使用<xref:System.Array.Rank%2A>屬性來判斷陣列中有多少維度。  
  
## <a name="working-with-dimensions"></a>使用維度  
 您指定的陣列項目透過提供*索引*或*註標*的每一個維度。 項目是從索引 0 到最高的索引，該維度的每個維度連續字元。  
  
 下圖顯示的不同陣序規範陣列概念的結構。 在圖例中的每個項目會顯示存取它的索引值。 例如，您可以存取二維陣列的第二個資料列的第一個項目指定的索引`(1, 0)`。  
  
 ![一個 &#45;示意圖; 二維陣列](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")  
一維陣列  
  
 ![兩個 &#45;示意圖; 二維陣列](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")  
二維陣列  
  
 ![三個 &#45;示意圖; 二維陣列](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")  
三維陣列  
  
### <a name="one-dimension"></a>一個維度  
 許多陣列有只有一個維度，例如每個年齡的人數。 指定元素的唯一需求為該元素保留計數的年齡。 因此，這類陣列會使用一個索引。 下列範例宣告變數，以保留*一維陣列*年齡的計算歲 0 到 120。  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a>兩個維度  
 某些陣列有兩個維度，例如辦公室校園每個建立的每個樓層數目。 項目的規格需要的大樓號碼和樓層，而且每個項目會保存組合的建築物和樓層計數。 因此，這類陣列會使用兩個索引。 下列範例宣告變數，以保留*二維陣列*office 計數，0 到 40 建築物和樓層 0 到 5。  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 二維陣列也稱為*矩形陣列*。  
  
### <a name="three-dimensions"></a>三個維度  
 有些陣列有三個維度，例如在 3d 空間中的值。 這類陣列會使用三個索引，在此情況下表示 x、 y 和 z 座標的實體空間。 下列範例宣告變數，以保留*三維陣列*的空中溫度三維的磁碟區中的各個點上。  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a>三個以上的維度  
 雖然陣列可以有 32 個維度，很少會有三個以上。  
  
> [!NOTE]
>  當您將維度加入至陣列時，陣列所需的總儲存空間會增加相當大，因此請小心使用多維陣列。  
  
## <a name="using-different-dimensions"></a>使用不同的維度  
 假設您想要追蹤銷售金額加總月的每一天。 您可能會宣告一維陣列 31 項目時，其中每一天的月份，如下列範例會顯示。  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 現在假設您想要追蹤之相同資訊不僅可針對每一天的月份，也包含一年的每個月。 您可能會宣告具有和二維陣列 （如月份） 12 列 31 個資料行 （適用於天），如下列範例所示。  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 現在假設您決定要讓您的陣列會保留一年以上的資訊。 如果您想要追蹤 5 年的銷售金額加總，您可以宣告一個三維陣列層級 5、 12 個資料列，與 31 個資料行，如下列範例所示。  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 請注意，因為每個索引會從 0 變化，其最大值，每個維度`salesAmounts`宣告為所需的長度小於該維度。 請注意，陣列的大小會隨著每個新的維度。 前述範例中的三個大小分別為 31、 372 和 1860 個元素。  
  
> [!NOTE]
>  您可以建立陣列，而不使用`Dim`陳述式或`New`子句。 例如，您可以呼叫<xref:System.Array.CreateInstance%2A>方法或另一個元件可以通過您的程式碼以這種方式建立的陣列。 這類陣列可以具有下限不是 0。 您可以一律作為維度的下限使用測試<xref:System.Array.GetLowerBound%2A>方法或`LBound`函式。  
  
## <a name="see-also"></a>另請參閱  
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [陣列的疑難排解](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)

---
title: "Array Dimensions in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "dimensions, arrays"
  - "arrays [Visual Basic], dimensions"
  - "arrays [Visual Basic], rectangular"
  - "arrays [Visual Basic], rank"
  - "rectangular arrays"
  - "ranking, arrays"
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Array Dimensions in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

「*維度*」\(Dimension\) 是用來變更陣列元素規格的方向。  保留該月份每天銷售總額的陣列具有一個維度 \(該月的日期\)。  保留該月份每天之部門銷售總額的陣列具有兩個維度 \(部門編號和該月的日期\)。  陣列所具有的維度數稱為它的「*陣序*」\(Rank\)。  
  
> [!NOTE]
>  您可以使用 <xref:System.Array.Rank%2A> 屬性來判斷陣列有多少維度。  
  
## 使用維度  
 您可以藉由提供每個陣列元素維度的「*索引*」\(Index\) 或「*註標*」\(Subscript\)，來指定陣列元素。  沿著每個維度 \(從索引 0 到該維度的最高索引\) 的索引會是連續的。  
  
 下列圖例顯示具有不同陣序之陣列的概念結構。  圖例中的每個元素都會顯示用來存取該元素的索引值。  例如，可藉由指定索引 `(1, 0)`，來存取二維陣列中第二列的第一個元素。  
  
 ![一維陣列示意圖](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.png "ArrayExDimOne")  
一維陣列  
  
 ![二維陣列示意圖](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")  
二維陣列  
  
 ![三維陣列示意圖](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.png "ArrayExDimThree")  
三維陣列  
  
### 一維  
 許多陣列只會有一個維度 \(例如每個年齡的人數\)。  指定元素的唯一需求就是該元素保留其計數的年齡。  因此，這類陣列只會使用一個索引。  下列範例會宣告一個變數，以保留 0 歲到 120 歲之年齡計數的「*一維陣列*」\(One\-Dimensional Array\)。  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### 二維  
 某些陣列會具有兩個維度，例如校園中每棟建築物之每個樓層的辦公室數目。  元素規格需要有建築物編號和樓層，而每個元素則會保留該建築物和樓層組合的計數。  因此，這類陣列會使用兩個索引。  下列範例會宣告一個變數，以保留辦公室計數的「*二維陣列*」\(Two\-Dimensional Array\)，建築物 0 到 40 和樓層 0 到 5。  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 二維陣列也稱為「*矩形陣列*」\(Rectangular Array\)。  
  
### 三維  
 有些陣列會具有三維，例如三維空間中的值。  這類陣列會使用三個索引，在此情況下，這三個索引分別表示實體空間的 x、y 和 z 座標。  下列範例會宣告一個變數，以保留用三維量的各個點數來表示「*三維陣列*」\(Three\-Dimensional Array\) 的氣溫。  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### 三個以上的維度  
 雖然陣列最多可有 32 個維度，但很少會有三個以上的維度。  
  
> [!NOTE]
>  將維度加入至陣列時，陣列所需的總儲存體會急遽增加，因此請謹慎使用多維陣列。  
  
## 使用不同的維度  
 假設想要追蹤這個月每天的銷售量。  您可能會宣告具有 31 個元素 \(該月的每一天一個元素\) 的一維陣列，如下列範例所示。  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 現在假設您不只想要追蹤某個月每天的相同資訊，也要追蹤那一年度每個月的相同資訊。  您可以宣告具有 12 列 \(用於月份\) 和 31 欄 \(用於天數\) 的二維陣列，如下列範例所示。  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 現在假設您決定要讓陣列保留一年以上的資訊。  如果您想要追蹤 5 年的銷售額，則可宣告具有 5 層、12 列和 31 欄的三維陣列，如下列範例所示。  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 請注意，因為每個索引都不同 \(從 0 到其最大值\)，所以 `salesAmounts` 的每個維度都以小於該維度之必要長度減一的值來宣告。  也請注意，陣列大小會隨著每個新維度而增加。  上面範例中的三個大小分別是 31、372 和 1,860 個元素。  
  
> [!NOTE]
>  在不使用 `Dim` 陳述式或 `New` 子句的情況下，也可以建立陣列。  例如，您可以呼叫 <xref:System.Array.CreateInstance%2A> 方法，或另一個元件可將用此方式建立的陣列傳遞給程式碼。  這類陣列可以有 0 以外的下限。  您可以一律使用 <xref:System.Array.GetLowerBound%2A> 方法或 `LBound` 函式來測試維度下限。  
  
## 請參閱  
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Troubleshooting Arrays](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
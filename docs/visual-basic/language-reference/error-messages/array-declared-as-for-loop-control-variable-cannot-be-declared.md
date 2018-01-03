---
title: "宣告為 for 迴圈控制變數的陣列不能宣告它的初始大小"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords: BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef36f14d5323a4592afe59573e249d8cfb218df9
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a>宣告為 for 迴圈控制變數的陣列不能宣告它的初始大小
A`For Each`迴圈會使用陣列做為其*元素*反覆運算變數，但初始化該陣列。  
  
 下列陳述式會顯示產生此錯誤的方式。  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 第一個`For Each`陳述式是正確的方式來存取元素的`arrayList`。 第二個`For Each`陳述式會產生這個錯誤。  
  
 **錯誤 ID:** BC32039  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   從宣告中移除初始化*元素*反覆運算變數。  
  
## <a name="see-also"></a>請參閱  
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [集合](../../../standard/collections/index.md)

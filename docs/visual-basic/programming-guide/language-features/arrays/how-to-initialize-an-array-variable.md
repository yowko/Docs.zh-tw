---
title: "How to: Initialize an Array Variable in Visual Basic | Microsoft Docs"
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
  - "variables [Visual Basic], initializing"
  - "arrays [Visual Basic], variables"
  - "arrays [Visual Basic], initializing"
  - "arrays [Visual Basic], declaring"
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
caps.latest.revision: 42
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 42
---
# How to: Initialize an Array Variable in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您會將陣列常值包含在 `New` 子句中，並指定陣列的初始值，以初始化陣列變數。  您可以指定類型，或允許從陣列常值中的值推斷類型。  如需如何推斷類型的詳細資訊，請參閱 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)中的＜在陣列填入初始值＞。  
  
### 若要使用陣列常值初始化陣列變數  
  
-   在 `New` 子句中，或者是您指派陣列值時，在大括號 \(`{}`\) 內提供元素值。  下列範例示範用於宣告、建立和初始化變數的數種方式，讓變數所包含的陣列元素為類型 `Char`。  
  
     [!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/how-to-initialize-an-arr_1.vb)]  
  
     執行每個陳述式之後，所建立的陣列長度為 3，從索引 0 到索引 2 的元素都有初始值。  如果同時提供上限和元素值，則必須為索引 0 到上限的每個元素加入值。  
  
     請注意，如果您以陣列常值提供元素值，則不必指定索引上限。  如果沒有指定索引上限，則會依據陣列常值中值的數目推斷陣列大小。  
  
### 若要使用陣列常值初始化多維陣列變數  
  
-   在大括號 \(`{}`\) 內使用大括號巢狀化數值。  請確認這些巢狀陣列常值全都會推斷為相同類型和長度的陣列。  下列程式碼範例會顯示數種多維陣列初始化的範例。  
  
     [!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/how-to-initialize-an-arr_2.vb)]  
  
-   您可以明確指定陣列界限，或是省略界限資訊讓編譯器依據陣列常值中的值推斷陣列界限。  如果您提供上限與值，則必須包含每個維度內從索引 0 到上限的每個元素值。  下列範例示範用於宣告、建立和初始化變數的數種方式，讓變數所包含的二維陣列元素為類型 `Short`。  
  
     [!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/how-to-initialize-an-arr_3.vb)]  
  
     執行每個陳述式後，所建立的陣列包含 6 個初始化元素，其索引為 `(0,0)`、`(0,1)`、`(0,2)`、`(1,0)`、`(1,1)` 和 `(1,2)`。  每個陣列位置都包含值 `10`。  
  
-   下列範例會逐一查看多維陣列。  在以 Visual Basic 撰寫的 Windows 主控台應用程式中，將程式碼貼入 `Sub Main()` 方法中。  最後一個註解會顯示輸出。  
  
     [!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/how-to-initialize-an-arr_4.vb)]  
  
### 若要使用陣列常值初始化不規則陣列變數  
  
-   在大括號 \(`{}`\) 內巢狀化物件值。  雖然您也可以巢狀化用於指定不同長度陣列的陣列常值，但在不規則陣列 \(Jagged Array\) 的案例中，請確認巢狀陣列常值是以括號 \(`()`\) 括住的。  括號會強制評估巢狀陣列常值，而產生的陣列就會用來做為不規則陣列的初始值。  下列程式碼範例會顯示 2 個不規則陣列初始化範例。  
  
     [!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/how-to-initialize-an-arr_5.vb)]  
  
-   下列範例會逐一查看不規則陣列。  在以 Visual Basic 撰寫的 Windows 主控台應用程式中，將程式碼貼入 `Sub Main()` 方法中。程式碼的最後一個註解會顯示輸出。  
  
     [!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/how-to-initialize-an-arr_6.vb)]  
  
## 請參閱  
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Troubleshooting Arrays](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
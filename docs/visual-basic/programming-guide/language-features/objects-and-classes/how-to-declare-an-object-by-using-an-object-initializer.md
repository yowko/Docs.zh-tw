---
title: "How to: Declare an Object by Using an Object Initializer (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declaring objects using object initializer"
  - "object initializers [Visual Basic]"
  - "initializers [Visual Basic]"
  - "Video How tos, Visual Basic"
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Declare an Object by Using an Object Initializer (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

物件初始設定式可讓您在單一陳述式 \(Statement\) 中宣告及具現化類別 \(Class\) 的執行個體 \(Instance\)。  此外，您可以同時初始化執行個體的一個或多個成員，而不需要叫用 \(Invoke\) 參數型建構函式 \(Constructor\)。  
  
 當您使用物件初始設定式來建立具名型別的執行個體時，會呼叫類別的預設建構函式，接著按照您指定的順序初始化指定的成員。  
  
 下列程序顯示如何以三種不同的方式來建立 `Student` 類別的執行個體。  此類別具有姓氏、名字和年級屬性。  這三項宣告中的每一項都會建立 `Student` 的新執行個體，其 `First` 屬性設為 "Michael"、`Last` 屬性設為 "Tucker"，而其他所有屬性則設為預設值。  此程序中的每項宣告結果都符合下列不使用物件初始設定式的範例。  
  
 [!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]  
  
 如需 `Student` 類別的實作 \(Implementation\)，請參閱 [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)。  您可以複製該主題中的程式碼，以設定類別並建立要處理的 `Student` 物件。  
  
### 若要使用物件初始設定式建立具名類別的物件  
  
1.  如同您計劃使用建構函式一樣開始宣告。  
  
     `Dim student1 As New Student`  
  
2.  輸入關鍵字 `With`，後面接著以大括弧括住的初始設定清單。  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  在初始設定清單中，包含您想初始化的每個屬性並且指派其初始值。  屬性名稱前面必須有一個句號。  
  
     [!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]  
  
     您可以初始化類別的一個或多個成員。  
  
4.  此外，您也可以宣告類別的新執行個體，然後指派其值。  首先，宣告 `Student` 的執行個體：  
  
     `Dim student2 As Student`  
  
5.  以正常方式開始建立 `Student` 的執行個體。  
  
     `Dim student2 As Student = New Student`  
  
6.  依序輸入 `With` 和物件初始設定式，以初始化新執行個體的一個或多個成員。  
  
     [!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]  
  
7.  您可以省略 `As Student`，以簡化前一個步驟中的定義。  如果您這麼做，編譯器 \(Compiler\) 會使用區域型別推斷，判斷 `student3` 為 `Student` 的執行個體。  
  
     [!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]  
  
     如需詳細資訊，請參閱[Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
## 請參閱  
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)   
 [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
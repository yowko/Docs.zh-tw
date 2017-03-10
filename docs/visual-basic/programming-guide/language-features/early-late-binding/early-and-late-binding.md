---
title: "Early and Late Binding (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "02/25/2017"
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
  - "early binding"
  - "objects [Visual Basic], late-bound"
  - "objects [Visual Basic], early-bound"
  - "objects [Visual Basic], late bound"
  - "early binding, Visual Basic compiler"
  - "binding, late and early"
  - "objects [Visual Basic], early bound"
  - "Visual Basic compiler, early and late binding"
  - "late binding"
  - "late binding, Visual Basic compiler"
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Early and Late Binding (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

當物件指派給物件變數時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器會執行稱為 `binding` 的處理序。  當物件指派給宣告為特定物件型別的變數時，該物件即為「*早期繫結*」\(Early Bound\)。  早期繫結物件允許編譯器配置記憶體，並在應用程式執行之前執行其他最佳化。  例如，下列程式碼片斷將變數宣告為型別 <xref:System.IO.FileStream>：  
  
 [!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#90)]  
  
 由於 <xref:System.IO.FileStream> 是特定物件型別，因此指派給 `FS` 的執行個體 \(Instance\) 是早期繫結。  
  
 相對來說，當物件指派給宣告為 `Object` 型別的變數時，該物件即為「*晚期繫結*」\(Late Bound\)。  此型別的物件可儲存任何物件的參考，但缺少早期繫結物件的優點。  例如，下列程式碼片斷宣告物件變數以儲存由 `CreateObject` 函式所傳回的物件：  
  
 [!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/LateBinding.vb#91)]  
  
## 早期繫結的優點  
 可能的話，您最好使用早期繫結物件，因為它們允許編譯器達到重要的最佳化，以產生更有效率的應用程式。  早期繫結物件明顯比晚期繫結物件快速，而且會藉由確切說明正在使用哪些物件來使您的程式碼更容易讀取與維護。  早期繫結的另一優點為：它啟用數種有用的功能，如自動程式碼完成和動態說明，因為 [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs-md.md)] 整合式開發環境 \(IDE\) 可準確判斷編輯程式碼時所使用的物件型別。  早期繫結減少執行階段錯誤的次數和嚴重性，因為它允許編譯器在編譯程式時報告錯誤。  
  
> [!NOTE]
>  晚期繫結只能使用於存取宣告為 `Public` 的型別成員。  存取宣告為 `Friend` 或 `Protected Friend` 的成員會導致執行階段錯誤。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>   
 [Object Lifetime: How Objects Are Created and Destroyed](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)
---
title: "Arrays declared as structure members cannot be declared with an initial size | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc31043"
  - "bc31043"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31043"
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Arrays declared as structure members cannot be declared with an initial size
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

結構中的陣列是以初始大小來宣告。  您無法初始化任何結構項目，而宣告陣列大小即是初始化的一種形式。  
  
 **錯誤 ID︰**BC31043  
  
### 若要更正這個錯誤  
  
1.  請在結構中將陣列定義為動態 \(即無初始大小\)。  
  
2.  如果您需要特定大小的陣列，可利用 [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) 在程式碼執行時重新設定動態陣列的大小。  下列範例將說明這點。  
  
    ```  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## 請參閱  
 [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [How to: Declare a Structure](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
---
title: "程式結構和程式碼慣例 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "編碼慣例"
  - "Visual Basic 程式碼，編碼慣例"
  - "編碼慣例，Visual Basic"
  - "程式，結構"
  - "程式結構"
  - "命名慣例，Visual Basic"
  - "最佳做法，編碼慣例"
  - "慣例，Visual Basic 編碼"
  - "Visual Basic 程式碼"
  - "程式設計，Visual Basic 編碼慣例"
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 程式結構和程式碼慣例 (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

本節會簡介典型的 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 程式結構、提供簡單的 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 程式 \("Hello, World"\)，以及討論 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 程式碼慣例。  程式碼慣例是一些建議，這些建議的重點不在程式的邏輯上，而是在程式的實體結構與外觀。  遵守這些建議將使您的程式碼更易於閱讀、了解與維護。  程式碼慣例主要包含以下項目：  
  
-   標記與註解程式碼的標準化格式  
  
-   程式碼間距、格式與縮排的方針  
  
-   物件、變數與程序的命名慣例  
  
 下列主題會展示 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 程式的程式設計方針，並附有正確使用方式的範例。  
  
## 在本節中  
 [Structure of a Visual Basic Program](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 提供會構成 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 程式的項目概觀。  
  
 [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 討論充當應用程式之起始點和整體控制的程序。  
  
 [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 討論如何參考其他組件中的物件。  
  
 [Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 描述命名空間如何在組件中組織物件。  
  
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 提供命名程序、常數、變數、引數和物件的一般性方針。  
  
 [Visual Basic Coding Conventions](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 檢閱用於開發本文件中之範例的方針。  
  
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 說明如何選擇性地編譯特定的程式碼區塊，使編譯器忽略其他程式碼區塊。  
  
 [如何：在程式碼中中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 說明如何將長的陳述式分割為數行，以及將短的陳述式合併成一行。  
  
 [How to: Collapse and Hide Sections of Code](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 顯示如何摺疊和隱藏 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 程式碼編輯器中的程式碼區段。  
  
 [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 顯示如何標記一行程式碼加以識別，以便與陳述式 \(如 `On Error Goto`\) 搭配使用。  
  
 [Special Characters in Code](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 討論使用非數字與非字母字元的方式和時機。  
  
 [Comments in Code](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 討論如何在您的程式碼中加入描述性註解。  
  
 [Keywords as Element Names in Code](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 說明如何使用方括號 \(`[]`\) 來分隔同時也是 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 關鍵字的變數名稱。  
  
 [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 說明各種參考 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 程式項目的方法。  
  
 [Visual Basic Limitations](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 討論如何移除 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 內的已知編碼限制。  
  
## 相關章節  
 [Typographic and Code Conventions](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 提供 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 的標準編碼慣例。  
  
 [撰寫程式碼](/visual-studio/ide/writing-code-in-the-code-and-text-editor)  
 描述讓您更輕鬆撰寫及管理程式碼的功能。
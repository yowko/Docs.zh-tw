---
title: "程式結構和程式碼慣例 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions, Visual Basic
- programs, structure
- program structure
- naming conventions, Visual Basic
- best practices, coding conventions
- conventions, Visual Basic coding
- Visual Basic code
- programming, Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
caps.latest.revision: 21
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cd25d99d74bf1e4d416c9da63758f6ad04027258
ms.lasthandoff: 03/13/2017

---
# <a name="program-structure-and-code-conventions-visual-basic"></a>程式結構和程式碼慣例 (Visual Basic)
本節將介紹一般[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式結構，提供簡單的[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式，"Hello World"，並討論[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式碼慣例。 程式碼慣例是將焦點放不在程式的邏輯，但其實體結構和外觀上的建議。 後面，可讓您的程式碼容易閱讀、 瞭解與維護。 還有其他程式碼慣例可以包括︰  
  
-   標籤與註解的程式碼的標準化的格式。  
  
-   間距、 格式和縮排程式碼的指導方針。  
  
-   物件、 變數和程序的命名慣例。  
  
 下列主題提供一組程式設計方針[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]計劃以及良好的使用方式的範例。  
  
## <a name="in-this-section"></a>本章節內容  
 [Visual Basic 程式的結構](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 提供概觀，構成項目[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式。  
  
 [在 Visual Basic 中的 main 程序](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 討論可做為開始點和整體控制您的應用程式的程序。  
  
 [參考和 Imports 陳述式](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 討論如何參考其他組件中的物件。  
  
 [在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 描述如何命名空間組織內的組件的物件。  
  
 [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 包含命名程序、 常數、 變數、 引數和物件的一般指導方針。  
  
 [Visual Basic 編碼慣例](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 檢閱的指導方針來開發這份文件中的範例。  
  
 [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 說明如何選擇性地編譯特定程式碼區塊，而使編譯器忽略其他人。  
  
 [如何：在程式碼內中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 示範如何分割成多行的長陳述式和合併在一行的簡短陳述式。  
  
 [如何：摺疊和隱藏程式碼區段](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 示範如何摺疊和隱藏程式碼中的區段[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式碼編輯器。  
  
 [如何：標記陳述式](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 示範如何將標記來識別它的使用陳述式這類的程式碼行`On Error Goto`。  
  
 [程式碼中的特殊字元](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 示範如何以及在何處使用非數字與非字母字元。  
  
 [程式碼中的註解](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 討論如何將描述性註解加入至您的程式碼。  
  
 [程式碼中以關鍵字做為項目名稱](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 描述如何使用方括號 (`[]`) 來分隔變數名稱，也是[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]關鍵字。  
  
 [Me、My、MyBase 和 MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 描述各種參考的元素[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式。  
  
 [Visual Basic 的限制](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 討論已知的程式碼撰寫限制內移除[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。  
  
## <a name="related-sections"></a>相關章節  
 [印刷樣式與程式碼慣例](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 提供標準的程式碼撰寫慣例[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。  
  
 [撰寫程式碼](https://docs.microsoft.com/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 描述功能，可讓您更輕鬆地撰寫並管理您的程式碼。

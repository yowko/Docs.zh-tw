---
title: "Structure of a Visual Basic Program | Microsoft Docs"
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
  - "conditional compilation, Visual Basic"
  - "program structure, Visual Basic"
  - "procedures, structure"
  - "Visual Basic code, program structure"
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Structure of a Visual Basic Program
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 程式是從標準建置組塊 \(Building Blocks\) 建置而成。  一個「*方案*」可以包含一個或多個專案，  而一個「*專案*」可以包含一個或多個組件。  每個「*組件*」則是由一個或多個原始程式檔 \(Source File\) 編譯而來。  「*原始程式檔*」提供類別、結構、模組和介面的定義與實作，最後會包含所有的程式碼。  
  
 如需這些 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 程式建置組塊的詳細資訊，請參閱[專案和方案](/visual-studio/ide/solutions-and-projects-in-visual-studio)和[組件和全域組件快取](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 檔案層級的程式設計項目  
 啟動專案或檔案並開啟程式碼編輯器，您將會看到有些程式碼已出現在適當的位置並依照正確的順序排列。  您所撰寫的任何程式碼都應該依照下列順序：  
  
1.  `Option` 陳述式  
  
2.  `Imports` 陳述式  
  
3.  `Namespace` 陳述式和命名空間層級的項目  
  
 如果以不同的順序輸入陳述式，會導致編譯錯誤。  
  
 程式也可以包含條件式編譯陳述式。  您可以在原始程式檔中，將這些陳述式穿插在上述的陳述式順序之間。  
  
### Option 陳述式  
 `Option` 陳述式是用來為後續的程式碼建立基本規則，以協助避免語法以及邏輯錯誤。  [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) 可以確保所有變數的宣告和拼寫都正確，減少偵錯時間。  當您使用不同資料型別的變數時，[Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)有助於將可能導致的邏輯錯誤與資料遺失降至最低。  [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)則指定字串相互比較的方式，可以根據 `Binary` 值或 `Text` 值進行比較。  
  
### Imports 陳述式  
 您可以納入 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)，以匯入在專案外部定義的名稱。  `Imports` 陳述式允許您的程式碼不需檢查，即可參考匯入命名空間中所定義的類別與其他型別。  您可以使用多個 `Imports` 陳述式，數量視需求而定。  如需詳細資訊，請參閱 [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)。  
  
### Namespace 陳述式  
 命名空間可以協助您將程式設計項目進行組織和分類，讓群組和存取變得更容易。  使用 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)時，可以將它後面的陳述式分類到特定命名空間。  如需詳細資訊，請參閱 [Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。  
  
### 條件式編譯陳述式  
 條件式編譯陳述式幾乎可以出現在原始程式檔的任何地方。  它們會根據特定條件，在編譯時期納入或排除部分的程式碼。  您也可以使用這些陳述式為應用程式偵錯，因為條件式程式碼只能執行於偵錯模式中。  如需詳細資訊，請參閱 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)。  
  
## 命名空間層級的程式設計項目  
 類別、結構和模組包含原始程式檔中的所有程式碼。  這些是「*命名空間層級*」項目，可以出現在命名空間中或原始程式檔層級。  它們會保留其他所有程式設計項目的宣告。  定義項目簽章 \(Signature\) 但不提供實作的介面，也會出現在模組層次。  如需模組層次項目的詳細資訊，請參閱下列主題：  
  
-   [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 命名空間層級的資料項目是列舉型別 \(Enumeration\) 和委派。  
  
## 模組層次的程式設計項目  
 可以保留可執行程式碼 \(在執行階段執行動作的陳述式\) 的程式設計項目只有程序、運算子、屬性和事件。  這些是程式的「*模組層次*」項目。  如需程序層級項目的詳細資訊，請參閱下列主題：  
  
-   [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 模組層次的資料項目是變數、常數、列舉型別和委派。  
  
## 程序層級的程式設計項目  
 「*程序層級*」項目大部分的內容都是可執行的陳述式，構成程式的執行階段程式碼。  所有可執行程式碼都必須位在某個程序中 \(`Function`、`Sub`、`Operator`、`Get`、`Set`、`AddHandler`、`RemoveHandler`、`RaiseEvent`\)。  如需詳細資訊，請參閱 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)。  
  
 程序層級的資料項目僅限於區域變數和常數。  
  
## Main 程序  
 `Main` 程序是當您的應用程式已載入時所執行的第一段程式碼。  `Main` 是您應用程式的起點，並具有整體控制的作用。  `Main` 共有四種形式：  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 這個程序最常見的形式是 `Sub Main()`。  如需詳細資訊，請參閱 [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)。  
  
## 請參閱  
 [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/zh-tw/9d030b60-e148-4366-a462-69532f02294c)   
 [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)   
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Visual Basic Limitations](../../../visual-basic/programming-guide/program-structure/limitations.md)
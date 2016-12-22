---
title: "/main | Microsoft Docs"
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
  - "main compiler option [Visual Basic]"
  - "/main compiler option [Visual Basic]"
  - "-main compiler option [Visual Basic]"
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /main
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定包含 `Sub Main` 程序的類別或模組。  
  
## 語法  
  
```  
/main:location  
```  
  
## 引數  
 `location`  
 必要項。  這是類別或模組的完整限定性條件，其中包含程式啟動時要呼叫的 `Sub Main` 程序。  它的形式可以是 **\/main:module** 或 **\/main:namespace.module**。  
  
## 備註  
 當您建立可執行檔或 WIndows 可執行程式時，請使用這個選項。  如果省略了 **\/main** 選項，編譯器 \(Compiler\) 就會在所有公用 \(Public\) 類別和模組中搜尋有效的共用 `Sub Main`。  
  
 如需對於`Main` 程序之各種形式的討論，請參閱 [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)。  
  
 當 `location` 是繼承自 <xref:System.Windows.Forms.Form> 的類別時，編譯器會提供預設的 `Main` 程序，在類別沒有 `Main` 程序時啟動應用程式。  這讓您可以在命令列中編譯於開發環境中建立的程式碼。  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### 若要在 Visual Studio 整合式開發環境中設定 \/main  
  
1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
     如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  按一下 \[**應用程式**\] 索引標籤。  
  
3.  確定未核取 \[**啟用應用程式架構**\] 核取方塊。  
  
4.  修改 \[**啟始物件**\] 方塊中的值。  
  
## 範例  
 下列程式碼會編譯 `T2.vb` 和 `T3.vb`，指定 `Sub Main` 程序可在 `Test2` 類別中找到。  
  
```  
vbc t2.vb t3.vb /main:Test2  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/zh-tw/9d030b60-e148-4366-a462-69532f02294c)   
 [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
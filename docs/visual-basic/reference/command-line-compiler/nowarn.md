---
title: "/nowarn | Microsoft Docs"
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
  - "nowarn compiler option [Visual Basic]"
  - "/nowarn compiler option [Visual Basic]"
  - "-nowarn compiler option [Visual Basic]"
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /nowarn
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

隱藏編譯器產生警告的能力。  
  
## 語法  
  
```  
/nowarn[:numberList]  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`numberList`|選擇項。  以逗號分隔的警告 ID 編號清單，編譯器不會顯示此清單。  如果未指定警告 ID，則不會顯示所有警告。|  
  
## 備註  
 `/nowarn` 選項會讓編譯器無法產生警告。  若不要顯示個別的警告，請將警告 ID 提供給其後接有冒號的 `/nowarn` 選項。  使用逗號來區隔多個警告編號。  
  
 您只需要指定警告識別項的數字部分。  例如，如果不想顯示 BC42024 \(未使用區域變數的警告\)，請指定 `/nowarn:42024`。  
  
 如需警告 ID 編號的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
||  
|-|  
|若要在 Visual Studio 整合式開發環境中設定 \/nowarn|  
|1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.  按一下 \[**編譯**\] 索引標籤。<br />3.  選取 \[**停用所有警告**\] 核取方塊，以停用所有警告。<br />     \-或\-<br />     若要停用特定警告，請從警告旁邊的下拉式清單中按一下 \[**無**\]。|  
  
## 範例  
 下列程式碼會編譯 `T2.vb`，而且不會顯示任何警告。  
  
```  
vbc /nowarn t2.vb  
```  
  
## 範例  
 下列程式碼會編譯 `T2.vb`，而且不會顯示未使用區域變數的警告 \(42024\)。  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)
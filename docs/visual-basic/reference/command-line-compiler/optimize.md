---
title: "/optimize | Microsoft Docs"
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
  - "optimize compiler option [Visual Basic]"
  - "/optimize compiler option [Visual Basic]"
  - "optimization, enabling"
  - "-optimize compiler option [Visual Basic]"
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /optimize
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

啟用或停用編譯器最佳化。  
  
## 語法  
  
```  
/optimize[ + | - ]  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`+`  &#124; `-`|選擇項。  `/optimize-` 選項會停用編輯器的最佳化功能。  `/optimize+` 選項則會啟用最佳化功能。  根據預設，最佳化功能是停用的。|  
  
## 備註  
 編譯器最佳化可使輸出檔更小、更快，而且更有效。  但是，由於最佳化會導致輸出檔中的程式碼重新排列，因此 `/optimize+` 可能會使偵錯更為困難。  
  
 所有以 `/target:module` 來為組件 \(Assembly\) 產生的模組，都必須使用與該組件相同的 `/optimize` 設定。  如需詳細資訊，請參閱 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)。  
  
 您可結合 `/optimize` 和 `/debug` 選項。  
  
||  
|-|  
|若要在 Visual Studio 整合式開發環境中設定 \/optimize|  
|1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。<br />     如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.  按一下 \[**編譯**\] 索引標籤。<br />3.  按一下 \[**進階**\] 按鈕。<br />4.  修改 \[**啟用最佳化**\] 核取方塊。|  
  
## 範例  
 下列程式碼會編譯 `T2.vb`，並啟用編譯器最佳化。  
  
```  
vbc t2.vb /optimize  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/debug](../../../visual-basic/reference/command-line-compiler/debug.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)
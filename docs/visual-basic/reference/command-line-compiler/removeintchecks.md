---
title: "/removeintchecks | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "removeintchecks"
  - "/removeintchecks"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "removeintchecks compiler option [Visual Basic]"
  - "/removeintchecks compiler option [Visual Basic]"
  - "-removeintchecks compiler option [Visual Basic]"
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# /removeintchecks
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

開啟或關閉整數運算的溢位錯誤檢查。  
  
## 語法  
  
```  
/removeintchecks[+ | -]  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`+`  &#124; `-`|選擇項。  `/removeintchecks-`選項會使編譯器檢查所有整數的溢位錯誤的計算。  預設值為 `/removeintchecks-`。<br /><br /> 指定 `/removeintchecks` 或 `/removeintchecks+` 可以防止錯誤檢查，並讓整數計算的速度更快。  不過，在沒有錯誤檢查的情況下，如果資料型別容量溢位，則由於沒有引發錯誤，所以可能會儲存不正確的結果。|  
  
||  
|-|  
|若要在 Visual Studio 整合式開發環境中設定 \/removeintchecks|  
|1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.  按一下 \[**編譯**\] 索引標籤。<br />3.  按一下 \[**進階**\] 按鈕。<br />4.  修改 \[**移除整數的溢位檢查**\] 方塊的值。|  
  
## 範例  
 下列程式碼會編譯 `Test.vb`，並關閉整數的溢位錯誤檢查。  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
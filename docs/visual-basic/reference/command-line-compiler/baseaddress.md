---
title: "/baseaddress | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/baseaddress"
  - "baseaddress"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-baseaddress compiler option [Visual Basic]"
  - "/baseaddress compiler option [Visual Basic]"
  - "baseaddress compiler option [Visual Basic]"
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /baseaddress
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

當建立 DLL 時，指定預設基底位址。  
  
## 語法  
  
```  
/baseaddress:address  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`address`|必要項。  DLL 的基底位址。  這個位址必須指定為十六進位數字。|  
  
## 備註  
 DLL 的預設基底位址是由 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 所設定。  
  
 請注意，這個位址中的低序位文字會捨去。  例如，如果您指定的是 0x11110001，這個數字就會調整為 0x11110000。  
  
 若要完成 DLL 的簽署程序，請使用強式命名工具 \(Sn.exe\) 的 `–R` 選項。  
  
 如果目標不是 DLL，則可略過這個選項。  
  
||  
|-|  
|若要在 Visual Studio IDE 中設定 \/baseaddress|  
|1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.  按一下 \[**編譯**\] 索引標籤。<br />3.  按一下 \[**進階**\]。<br />4.  修改 \[**DLL 基底位址：**\] 方塊的值。 **Note:**      除非目標是 DLL，否則 \[**DLL 基底位址：**\] 方塊是唯讀的。|  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)
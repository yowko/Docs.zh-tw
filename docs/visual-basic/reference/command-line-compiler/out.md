---
title: "/out (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/out compiler option [Visual Basic]"
  - "-out compiler option [Visual Basic]"
  - "out compiler option [Visual Basic]"
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# /out (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定輸出檔名稱。  
  
## 語法  
  
```  
/out:filename  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`filename`|必要項。  編譯器所建立的輸出檔名。  如果檔案名稱包含空格，請將名稱加上英文引號 \(" "\)。|  
  
## 備註  
 請指定要建立的檔案完整名稱和副檔名。  如果您不指定，則 .exe 檔案會從包含 `Sub Main` 程序的原始程式碼檔中取得其名稱，而 .dll 檔案會從第一個原始程式碼檔中取得其名稱。  
  
 如果您指定的檔名沒有 .exe 或 .dll 副檔名，編譯器會根據 `/target` 編譯器選項所指定的值，自動加上副檔名。  
  
||  
|-|  
|若要在 Visual Studio 整合式開發環境中設定 \/out|  
|1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.  按一下 \[**應用程式**\] 索引標籤。<br />3.  修改 \[**組件名稱**\] 方塊中的值。|  
  
## 範例  
 下列程式碼會編譯 `T2.vb`，並建立輸出檔 `T2.exe`。  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
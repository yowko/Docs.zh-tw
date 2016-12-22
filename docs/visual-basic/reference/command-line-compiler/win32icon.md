---
title: "/win32icon | Microsoft Docs"
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
  - "win32icon compiler option [Visual Basic]"
  - "-win32icon compiler option [Visual Basic]"
  - "/win32icon compiler option [Visual Basic]"
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /win32icon
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

將 .ico 檔案插入至輸出檔。  這個.ico檔案代表在 **檔案總管**的輸出檔。  
  
## 語法  
  
```  
/win32icon:filename  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`filename`|要加入至您的輸出檔的 .ico 檔案。  如果檔案名稱包含空格，請加上英文雙引號 \(" "\)。|  
  
## 備註  
 您可以使用 Microsoft Windows 資源編譯器 \(RC\) 來建立 .ico 檔案。  資源編譯器是在編譯 Visual C\+\+ 程式時叫用的，而 .ico 檔案則是用 .rc 檔案建立的。  `/win32icon` 和 `/win32resource` 是互斥 \(Mutually Exclusive\) 的選項。  
  
 請參閱 [\/linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md) 來參考 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 資源檔，或參閱 [\/resource](../../../visual-basic/reference/command-line-compiler/resource.md) 來附加 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 資源檔。  請參閱 [\/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) 來匯入 .res 檔。  
  
||  
|-|  
|若要在 Visual Studio IDE 中設定 \/win32icon|  
|1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.  按一下 \[**應用程式**\] 索引標籤。<br />3.  修改 \[**圖示**\] 方塊中的值。|  
  
## 範例  
 下列程式碼會編譯 `In.vb`，並附加 .ico 檔案 `Rf.ico`。  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
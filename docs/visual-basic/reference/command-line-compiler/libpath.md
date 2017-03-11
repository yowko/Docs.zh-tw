---
title: "/libpath | Microsoft Docs"
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
  - "libpath compiler option [Visual Basic]"
  - "/libpath compiler option [Visual Basic]"
  - "-libpath compiler option [Visual Basic]"
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# /libpath
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定參考組件的位置。  
  
## 語法  
  
```  
/libpath:dirList  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`dirList`|必要項。  如果在目前的工作目錄 \(您叫用編譯器時所在的目錄\) 或 Common Language Runtime 的系統目錄中都找不到參考的組件，編譯器所要查詢以分號分隔的目錄清單。  如果目錄名稱包含空格，請將名稱加上引號 \(" "\)。|  
  
## 備註  
 `/libpath` 選項會指定由 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md) 選項所參考的組件位置。  
  
 編譯器依據以下順序搜尋那些沒有完整路徑名稱的組件參考：  
  
1.  目前工作目錄。  就是從這個目錄叫用編譯器。  
  
2.  Common Language Runtime 的系統目錄。  
  
3.  `/libpath` 指定的目錄。  
  
4.  由 LIB 環境變數指定的目錄。  
  
 `/libpath` 選項具有附加特性，指定超過一次就會附加到任何先前的值。  
  
 使用 `/reference` 指定組件參考。  
  
||  
|-|  
|若要在 Visual Studio 整合式開發環境中設定 \/libpath|  
|1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.  按一下 \[**參考**\] 索引標籤。<br />3.  按一下 \[**參考路徑**\] 按鈕。<br />4.  在 \[**參考路徑**\] 對話方塊的 \[**資料夾：**\] 方塊中，輸入目錄名稱。<br />5.  按一下 \[**加入資料夾**\]。|  
  
## 範例  
 下列程式碼會編譯 `T2.vb` 以建立 .exe 檔案。  編譯器會在工作目錄 \(位於 C: 磁碟機的根目錄\)，以及 C: 磁碟機的 New Assemblies 目錄中查詢組件參考。  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## 請參閱  
 [組件和全域組件快取](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
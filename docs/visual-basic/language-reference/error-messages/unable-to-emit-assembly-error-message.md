---
title: "Unable to emit assembly: &lt;error message&gt; | Microsoft Docs"
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
  - "vbc30145"
  - "bc30145"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30145"
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Unable to emit assembly: &lt;error message&gt;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 編譯器呼叫組件連結器 \(Al.exe，也稱為 Alink\) 使用資訊清單產生組件，連結器在建立組件的發出階段回報錯誤。  
  
 **錯誤 ID︰**BC30145  
  
### 更正這個錯誤  
  
1.  檢查引用的錯誤訊息，並參考主題 [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/zh-tw/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)，以取得進一步說明和建議。  
  
2.  嘗試手動簽署組件，使用 [Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 或[Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)。  
  
3.  如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。  
  
### 手動簽署組件  
  
1.  使用 [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) 建立公開\/私密金鑰組檔案。  
  
     這個檔案的副檔名為 .snk。  
  
2.  從專案刪除產生錯誤的 COM 參考。  
  
3.  從 Windows \[開始\] 功能表，然後依序指向 \[程式集\]、\[Microsoft Visual Studio 2008\]、\[Visual Studio Tools\]，再按一下 \[Visual Studio 2008 命令提示字元\]。  
  
4.  移到您要放置組件包裝函式的目錄。  
  
5.  輸入下列程式碼。  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     您可能輸入的程式碼範例如下。  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     如果路徑或檔案包含空格，請使用雙引號 \("\)。  
  
6.  在 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 中，加入您剛建立之檔案的 .NET Assembly 參考。  
  
## 請參閱  
 [Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)   
 [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/zh-tw/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)   
 [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)   
 [如何：建立公開\/私密金鑰組](../Topic/How%20to:%20Create%20a%20Public-Private%20Key%20Pair.md)   
 [告訴我們](/visual-studio/ide/talk-to-us)
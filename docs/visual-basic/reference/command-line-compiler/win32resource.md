---
title: "/win32resource | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "/win32resource"
  - "win32resource"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/win32resource compiler option [Visual Basic]"
  - "-win32resource compiler option [Visual Basic]"
  - "win32resource compiler option [Visual Basic]"
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# /win32resource
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

將 Win32 資源檔插入至輸出檔。  
  
## 語法  
  
```  
/win32resource:filename  
```  
  
## 引數  
 `filename`  
 要加入至您的輸出檔的資源檔名稱。  如果檔案名稱包含空格，請加上英文雙引號 \(" "\)。  
  
## 備註  
 您可以使用 Microsoft Windows 資源編譯器 \(RC\) 來建立 Win32 資源檔。  
  
 Win32資源可包含可協助識別在 **檔案總管**的應用程式版本或點陣圖資訊。  如果您沒有指定 `/win32resource`，編譯器會依據組件 \(Assembly\) 版本來產生版本資訊。  `/win32resource` 和 `/win32icon` 是互斥 \(Mutually Exclusive\) 的選項。  
  
 請參閱 [\/linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md) 來參考 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 資源檔，或參閱 [\/resource](../../../visual-basic/reference/command-line-compiler/resource.md) 來附加 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 資源檔。  
  
> [!NOTE]
>  `/win32resource` 選項無法在 Visual Studio 開發環境內使用；只有在命令列編譯時才能使用。  
  
## 範例  
 下列程式碼會編譯 `In.vb`，並附加 Win32 資源檔 `Rf.res`：  
  
```  
vbc /win32resource:rf.res in.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
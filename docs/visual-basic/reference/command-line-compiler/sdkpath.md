---
title: "/sdkpath | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "sdkpath"
  - "/sdkpath"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-sdkpath compiler option [Visual Basic]"
  - "/sdkpath compiler option [Visual Basic]"
  - "sdkpath compiler option [Visual Basic]"
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# /sdkpath
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。  
  
## 語法  
  
```  
/sdkpath:path  
```  
  
## 引數  
 `path`  
 包含編譯用之 Mscorlib.dll 和 Microsoft.VisualBasic.dll 版本的目錄。  路徑載入後才會進行驗證。  如果目錄名稱包含空格，請加上雙引號 \(" "\)。  
  
## 備註  
 這個選項會通知 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器，從非預設的位置載入 Mscorlib.dll 和 Microsoft.VisualBasic.dll 檔案。  `/sdkpath`  選項在設計上，是要與 [\/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md) 搭配使用。  [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] 會使用不同版本的支援程式庫，以避免使用到裝置上沒有的型別和語言功能。  
  
> [!NOTE]
>  `/sdkpath` 選項無法在 Visual Studio 開發環境內使用；只有在命令列編譯時才能使用。  載入 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 裝置專案時，才會設定 `/sdkpath` 選項。  
  
 您可以使用 `/vbruntime` 編譯器選項指定編譯器不應參考 Visual Basic 執行階段程式庫來進行編譯。  如需詳細資訊，請參閱 [\/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)。  
  
## 範例  
 下列的程式碼會使用 C 磁碟中 [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] 預設安裝目錄下的 Mscorlib.dll 和 Microsoft.VisualBasic.dll 版本，利用 [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] 來編譯 `Myfile.vb`。  您通常可使用最新版的 [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)]。  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)   
 [\/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
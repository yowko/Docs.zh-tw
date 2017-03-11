---
title: "/vbruntime | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbruntime"
  - "/vbruntime"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "vbruntime compiler option [Visual Basic]"
  - "-vbruntime compiler option [Visual Basic]"
  - "/vbruntime compiler option [Visual Basic]"
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# /vbruntime
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定編譯器應該不使用 Visual Basic 執行階段程式庫的參考來進行編譯，還是使用特定執行階段程式庫的參考來進行編譯。  
  
## 語法  
  
```  
/vbruntime:{ - | + | * | path }  
```  
  
## 引數  
 \-  
 不使用 Visual Basic 執行階段程式庫的參考來進行編譯。  
  
 \+  
 使用預設 Visual Basic 執行階段程式庫的參考來進行編譯。  
  
 \*  
 不使用 Visual Basic 執行階段程式庫參考來進行編譯，並且將 Visual Basic 執行階段程式庫中的核心功能內嵌到組件中。  
  
 `path`  
 使用指定之程式庫 \(DLL\) 的參考來進行編譯。  
  
## 備註  
 `/vbruntime` 編譯器選項可讓您指定編譯器不應使用 Visual Basic 執行階段程式庫的參考來進行編譯。  如果您不使用 Visual Basic 執行階段程式庫的參考進行編譯，則會針對產生 Visual Basic 執行階段 Helper 呼叫的程式碼或語言建構來記錄錯誤或警告   \(「*Visual Basic 執行階段 Helper*」是在 Microsoft.VisualBasic.dll 中定義的函式，在執行階段會呼叫這個函式以執行特定語意\)。  
  
 `/vbruntime+` 選項與未指定 `/vbruntime` 參數會產生相同的行為。  您可以使用 `/vbruntime+` 選項覆寫先前的 `/vbruntime` 參數。  
  
 大部分的物件的`My`型別都無法使用，當您使用`/vbruntime-`或`vbruntime:``path`選項。  
  
## 嵌入 Visual Basic 執行階段核心功能  
 `/vbruntime*` 選項允許您不使用執行階段程式庫的參考來進行編譯。  相反的，Visual Basic 執行階段程式庫的核心功能會內嵌在使用者組件中。  如果未包含Visual Basic的執行階段的平台上執行的程式應用程式，您可以使用此選項。  
  
 已內嵌下列執行階段成員：  
  
-   <xref:Microsoft.VisualBasic.CompilerServices.Conversions> 類別  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> 方法  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> 方法  
  
-   <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> 方法  
  
-   <xref:Microsoft.VisualBasic.Constants.vbBack> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCr> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCrLf> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbFormFeed> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbLf> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNewLine> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullChar> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullString> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbTab> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbVerticalTab> 常數  
  
-   某些物件的`My`型別  
  
 如果您使用 `/vbruntime*` 選項編譯，並且您的程式碼參考未內嵌核心功能之 Visual Basic 執行階段庫中的成員，則編譯器會傳回錯誤，表示該成員無法使用。  
  
## 參考指定的程式庫  
 您可以使用 `path` 引數，利用自訂執行階段程式庫 \(而非預設 Visual Basic 執行階段程式庫\) 的參考來進行編譯。  
  
 如果 `path` 引數的值是 DLL 的完整路徑，則編譯器會使用該檔案做為執行階段程式庫。  如果 `path` 引數的值不是 DLL 的完整路徑，則 Visual Basic 編譯器會先搜尋目前資料夾中已識別的 DLL，  接著會在您已經使用 [\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) 編譯器選項指定的路徑中進行搜尋。  如果未使用 `/sdkpath` 編譯器選項，則編譯器會在 .NET Framework 資料夾 \(`%systemroot%\Microsoft.NET\Framework\versionNumber`\) 中搜尋已識別的 DLL。  
  
## 範例  
 下列範例將說明如何使用 `/vbruntime` 選項，搭配自訂程式庫的參考進行編譯。  
  
```  
vbc /vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## 請參閱  
 [Visual Basic 核心 – 在 Visual Studio 2010 SP1 中的新編譯模式](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
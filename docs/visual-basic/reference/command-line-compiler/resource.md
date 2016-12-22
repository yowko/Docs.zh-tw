---
title: "/resource (Visual Basic) | Microsoft Docs"
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
  - "/resource compiler option [Visual Basic]"
  - "-resource compiler option [Visual Basic]"
  - "/res compiler option [Visual Basic]"
  - "res compiler option [Visual Basic]"
  - "-res compiler option [Visual Basic]"
  - "resource compiler option [Visual Basic]"
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /resource (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

將 Managed 資源嵌入至組件。  
  
## 語法  
  
```  
/resource:filename[,identifier[,public|private]]  
' -or-  
/res:filename[,identifier[,public|private]]  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`filename`|必要項。  要內嵌至輸出檔的資源檔名稱。  依預設，`filename` 在組件中是公用的。  如果檔案名稱包含空格，請加上英文雙引號 \(" "\)。|  
|`identifier`|選擇項。  資源的邏輯名稱；用來載入資源的名稱。  預設值是檔案的名稱。  或者，您可以在組件資訊清單中指定資源是公用的 \(Public\) 或私用的 \(Private\)，方法如下所示：`/res:``filename.res`、`myname.res`、`public`|  
  
## 備註  
 請使用 `/linkresource` 將資源連結至組件，而非將資源檔置於輸出檔中。  
  
 如果 `filename` 是由 [Resgen.exe \(Resource File Generator\)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) 或在開發環境中所建立的 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 資源檔，則可以使用 <xref:System.Resources> 命名空間 \(Namespace\) 內的成員來存取 \(如需詳細資訊，請參閱 <xref:System.Resources.ResourceManager>\)。  若要在執行階段存取其他所有資源，請使用下列其中一個方法：<xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>、<xref:System.Reflection.Assembly.GetManifestResourceNames%2A> 或 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>。  
  
 `/resource`  的簡短形式為 `/res`。  
  
 如需有關如何設定資訊`/resource`在 Visual Studio 的 IDE 中，請參閱[管理應用程式資源 \(.NET\)](/visual-studio/ide/managing-application-resources-dotnet)。  
  
## 範例  
 下列程式碼會編譯 `In.vb`，並附加資源檔 `Rf.resource`。  
  
```  
vbc /res:rf.resource in.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)   
 [\/linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
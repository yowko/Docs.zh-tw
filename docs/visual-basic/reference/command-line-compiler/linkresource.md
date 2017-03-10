---
title: "/linkresource (Visual Basic) | Microsoft Docs"
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
  - "/linkresource compiler option [Visual Basic]"
  - "-linkresource compiler option [Visual Basic]"
  - "linkresource compiler option [Visual Basic]"
  - "/linkres compiler option [Visual Basic]"
  - "linkres compiler option [Visual Basic]"
  - "-linkres compiler option [Visual Basic]"
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# /linkresource (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

對 Managed 資源建立連結。  
  
## 語法  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## 引數  
 `filename`  
 必要項。  與組件連結的資源檔。  如果檔案名稱包含空格，請將名稱加上英文引號 \(" "\)。  
  
 `identifier`  
 選擇項。  資源的邏輯名稱。  用來載入資源的名稱。  預設值是檔案的名稱。  或者，您可以在組件資訊清單 \(Assembly Manifest\) 中指定檔案是公用的 \(Public\) 或私用的 \(Private\)，例如：`/linkres:filename.res,myname.res,public`。  依預設，`filename` 在組件中是公用的。  
  
## 備註  
 `/linkresource` 選項不會將資源檔內嵌於輸出檔中。請使用 `/resource` 選項來進行內嵌。  
  
 `/linkresource` 選項需要 `/target` 選項其中之一，而非 `/target:module`。  
  
 如果 `filename` 是由 [Resgen.exe \(Resource File Generator\)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) 或在開發環境中建立的 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 資源檔，則可以使用 <xref:System.Resources> 命名空間內的成員來存取   \(如需詳細資訊，請參閱 <xref:System.Resources.ResourceManager>\)。 若要在執行階段時存取所有其他資源，請使用 <xref:System.Reflection.Assembly> 類別 \(Class\) 中以 `GetManifestResource` 開頭的方法。  
  
 檔案名稱可以是任何檔案格式。  例如，您可能希望讓原生 DLL 成為組件的一部分，以便將它安裝到全域組件快取，並經由組件中的 Managed 程式碼存取。  
  
 `/linkresource` 的簡短形式為 `/linkres`。  
  
> [!NOTE]
>  `/linkresource` 選項無法從 Visual Studio 開發環境使用，只有在命令列編譯時才能使用。  
  
## 範例  
 下列程式碼會編譯 `In.vb`，並連結至資源檔 `Rf.resource`。  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [\/resource](../../../visual-basic/reference/command-line-compiler/resource.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
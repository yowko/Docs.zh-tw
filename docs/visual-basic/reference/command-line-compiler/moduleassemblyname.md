---
title: "/moduleassemblyname | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "moduleassemblyname compiler option [Visual Basic]"
  - "/moduleassemblyname compiler option [Visual Basic]"
  - "-moduleassemblyname compiler option [Visual Basic]"
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /moduleassemblyname
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定此模組所屬的組件 \(Assembly\) 名稱。  
  
## 語法  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`assembly_name`|此模組所屬的組件名稱。|  
  
## 備註  
 指定 `/target:module` 選項後，編譯器 \(Compiler\) 才會處理 `/moduleassemblyname` 選項。  這會導致編譯器建立模組。  編譯器所建立的模組僅適用於使用 `/moduleassemblyname` 選項指定的組件。  如果您將模組放在不同的組件中，則會發生執行階段錯誤。  
  
 符合下列條件時，才需要有 `/moduleassemblyname` 選項：  
  
-   模組中的資料型別需要存取參考組件中的 `Friend` 型別。  
  
-   參考組件已將 friend 組件的存取權授與給模組將建置在其中的組件。  
  
 如需建立模組的詳細資訊，請參閱 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)。  如需 friend 組件的詳細資訊，請參閱 [Friend 組件](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)。  
  
> [!NOTE]
>  `/moduleassemblyname` 選項無法在 Visual Studio 開發環境中使用，只有在命令提示字元編譯時才能使用。  
  
## 請參閱  
 [如何：建置多檔案組件](../Topic/How%20to:%20Build%20a%20Multifile%20Assembly.md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [\/main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)   
 [組件和全域組件快取](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Friend 組件](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)
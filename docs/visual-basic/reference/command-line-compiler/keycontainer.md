---
title: "/keycontainer | Microsoft Docs"
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
  - "-keycontainer compiler option [Visual Basic]"
  - "keycontainer compiler option [Visual Basic]"
  - "/keycontainer compiler option [Visual Basic]"
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# /keycontainer
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

為金鑰組指定金鑰容器名稱，以便為組件指定強式名稱。  
  
## 語法  
  
```  
/keycontainer:container  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`container`|必要項。  包含金鑰的容器檔案。  如果檔案名稱包含空格，請將此名稱加上雙引號 \(""\)。|  
  
## 備註  
 編譯器會將公開金鑰 \(Public Key\) 插入至組件資訊清單，並且利用私密金鑰簽署最後的組件，藉以建立可共用的元件。  若要產生金鑰檔，請在命令列中輸入 `sn -k` `file`。  `-i`  選項會將金鑰組 \(Key Pair\) 安裝到容器中。  如需詳細資訊，請參閱 [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)。  
  
 如果您使用 `/target:module` 進行編譯，該金鑰檔的名稱便會儲存在模組中，並會合併至使用 [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) 編譯組件時所建立的組件。  
  
 您也可以為任何 Microsoft Intermediate Language \(MSIL\) 模組，指定這個選項當做原始程式碼中的自訂屬性 \(<xref:System.Reflection.AssemblyKeyNameAttribute>\)。  
  
 您也可使用 [\/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) 將加密資訊傳給編譯器。  如果您想要部分簽署的組件，請使用 [\/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)。  
  
 如需組件簽署的詳細相關資訊，請參閱[建立和使用強式名稱的組件](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)。  
  
> [!NOTE]
>  `/keycontainer` 選項無法在 Visual Studio 開發環境內使用，只有在命令列編譯時才能使用。  
  
## 範例  
 下列程式碼會編譯原始程式檔 `Input.vb`，並指定金鑰容器。  
  
```  
vbc /keycontainer:key1 input.vb  
```  
  
## 請參閱  
 [組件和全域組件快取](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
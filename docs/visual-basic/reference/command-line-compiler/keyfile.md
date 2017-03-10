---
title: "/keyfile | Microsoft Docs"
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
  - "/keyfile compiler option [Visual Basic]"
  - "keyfile compiler option [Visual Basic]"
  - "-keyfile compiler option [Visual Basic]"
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# /keyfile
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定包含金鑰或金鑰組的檔案，以便為組件指定強式名稱。  
  
## 語法  
  
```  
/keyfile:file  
```  
  
## 引數  
 `file`  
 必要項。  包含金鑰的檔案。  如果檔案名稱包含空格，請將名稱加上英文引號 \(" "\)。  
  
## 備註  
 編譯器將公開金鑰插入至組件資訊清單，然後利用私密金鑰簽署最後的組件。  若要產生金鑰檔，請在命令列中輸入 `sn -k file`。  如需詳細資訊，請參閱 [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)。  
  
 如果您使用 `/target:module` 進行編譯，該金鑰檔的名稱便會儲存在模組中，並會合併至使用 [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) 編譯組件時所建立的組件。  
  
 您也可使用 [\/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) 將加密資訊傳給編譯器。  如果您想要部分簽署的組件，請使用 [\/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)。  
  
 您也可以在原始程式碼中，為任何 Microsoft Intermediate Language 模組指定這個選項當做自訂屬性 \(<xref:System.Reflection.AssemblyKeyFileAttribute>\)。  
  
 若在同一次編譯過程中指定 `/keyfile` 與 [\/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) \(不論是以命令列選項或是自訂屬性的方式\)，編譯器都會先試用金鑰容器。  如果這個動作成功，那麼組件就會使用金鑰容器中的資訊加以簽署。  如果編譯器找不到金鑰容器，它會嘗試使用 `/keyfile` 指定的檔案。  成功的話，組件會以金鑰檔內的資訊簽署，並且金鑰資訊將安裝於金鑰容器內 \(類似於 `sn -i`\)，以便在下次編譯時，金鑰容器可變為有效。  
  
 請注意，金鑰檔可能只包含公開金鑰。  
  
 如需組件簽署的詳細相關資訊，請參閱[建立和使用強式名稱的組件](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)。  
  
> [!NOTE]
>  從 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 開發環境內無法使用 `/keyfile` 選項，只能在透過命令列進行編譯時使用。  
  
## 範例  
 下列程式碼會編譯原始程式檔 `Input.vb`，並指定金鑰檔。  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## 請參閱  
 [組件和全域組件快取](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
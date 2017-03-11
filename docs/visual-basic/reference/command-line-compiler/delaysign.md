---
title: "/delaysign | Microsoft Docs"
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
  - "delaysign compiler option [Visual Basic]"
  - "/delaysign compiler option [Visual Basic]"
  - "-delaysign compiler option [Visual Basic]"
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# /delaysign
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定要對組件加上完整簽署還是部分簽署。  
  
## 語法  
  
```  
/delaysign[+ | -]  
```  
  
## 引數  
 `+` &#124; `-`  
 選擇項。  如果要完整簽名的組件，請使用 `/delaysign-`。  如果您想要將公開金鑰 \(Public Key\) 放在組件中，並保留空間供已簽署的雜湊使用，請使用 `/delaysign+`。  預設值為 `/delaysign-`。  
  
## 備註  
 `/delaysign` 選項除非與 [\/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) 或 [\/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) 一起使用，否則不會發生任何作用。  
  
 當您要求完整簽署的組件時，編譯器會雜湊包含資訊清單 \(組件中繼資料\) 的檔案，並且利用私密金鑰簽署該項雜湊。  所產生的數位簽章儲存在包含資訊清單的檔案中。  當延遲簽署組件時，編譯器不會計算和儲存簽章，但會保留檔案中的空間，以便稍後再加入簽章。  
  
 例如，藉由使用 `/delaysign+`，組織中的開發人員可以散發未簽署的組件測試版本，軟體測試人員可以將這個組件註冊於全域組件快取並加以使用。  當組件上的工作完成時，負責組織之私密金鑰的人員可以完整地簽署組件。  這種劃分會在允許所有開發人員使用組件的同時，保護組織的私密金鑰以防公開。  
  
 如需組件簽署的詳細相關資訊，請參閱[建立和使用強式名稱的組件](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)。  
  
### 若要在 Visual Studio 整合式開發環境中設定 \/delaysign  
  
1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  按一下 \[**簽署**\] 索引標籤。  
  
3.  在 \[**僅延遲簽署**\] 方塊中設定值。  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [\/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
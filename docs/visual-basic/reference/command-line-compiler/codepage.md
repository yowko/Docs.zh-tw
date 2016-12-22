---
title: "/codepage (Visual Basic) | Microsoft Docs"
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
  - "/codepage compiler option [Visual Basic]"
  - "codepage compiler option [Visual Basic]"
  - "-codepage compiler option [Visual Basic]"
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /codepage (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定編譯過程中所有原始程式碼檔案使用的字碼頁。  
  
## 語法  
  
```  
/codepage:id  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`id`|必要項。  編譯器會使用 `id` 所指定的字碼頁，來解譯原始程式檔的編碼。|  
  
## 備註  
 若要編譯特定編碼所儲存的原始程式碼，可使用 `/codepage` 來指定要使用哪個字碼頁。  `/codepage` 選項會套用到編譯中的所有原始程式碼檔案。  如需詳細資訊，請參閱[.NET Framework 中的字元編碼方式](../Topic/Character%20Encoding%20in%20the%20.NET%20Framework.md)。  
  
 如果使用具有簽章的目前 ANSI 字碼頁、Unicode 或 UTF\-8 來儲存原始程式碼檔案，則不需要 `/codepage` 選項。  根據預設，[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 會以目前的 ANSI 字碼頁儲存所有的原始程式碼檔，除非使用者在 \[**編碼方式**\] 對話方塊中指定另一種編碼方式。  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 使用 \[**編碼方式**\] 對話方塊來開啟用不同字碼頁儲存的原始程式碼檔案。  
  
> [!NOTE]
>  從 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 開發環境內無法使用 `/codepage` 選項，只能在透過命令列進行編譯時使用。  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
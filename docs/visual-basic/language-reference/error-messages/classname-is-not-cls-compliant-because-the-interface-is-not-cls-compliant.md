---
title: "&#39;&lt;classname&gt;&#39; is not CLS-compliant because the interface &#39;&lt;interfacename&gt;&#39; it implements is not CLS-compliant | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc40029"
  - "vbc40029"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40029"
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# &#39;&lt;classname&gt;&#39; is not CLS-compliant because the interface &#39;&lt;interfacename&gt;&#39; it implements is not CLS-compliant
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

當類別或介面衍生自或實作已標記為 `<CLSCompliant(False)>` 或未標記的型別時，類別或介面就會標記為 `<CLSCompliant(True)>`。  
  
 對於要符合 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 標準的類別或介面而言，其整個繼承階層都必須符合標準。  這表示它所繼承的每個型別，都必須直接或間接符合標準。  同樣地，如果類別實作一或多個介面，整個繼承階層架構都必須完全符合標準。  
  
 當您將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，可以將屬性的 `isCompliant` 參數設定為 `True` 或 `False`，表示符合標準或不符合標準。  這個參數沒有預設值，所以您必須提供預設值。  
  
 如果沒有將 <xref:System.CLSCompliantAttribute> 套用至項目，會被認為是不相容。  
  
 根據預設，這是一個警告訊息。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID：**BC40029  
  
### 若要更正這個錯誤  
  
-   如果您要求符合 CLS 標準，請在不同的繼承階層架構或實作 \(Implementation\) 配置中定義這個型別。  
  
-   如果您要求這個型別留在目前的繼承階層或實作配置中，請將 <xref:System.CLSCompliantAttribute> 從定義中移除，或將它標記為 `<CLSCompliant(False)>`。  
  
## 請參閱  
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
---
title: "Name &lt;namespacename&gt; in the root namespace &lt;fullnamespacename&gt; is not CLS-compliant | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc40039"
  - "bc40039"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40039"
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Name &lt;namespacename&gt; in the root namespace &lt;fullnamespacename&gt; is not CLS-compliant
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

組件 \(Assembly\) 已標示為 `<CLSCompliant(True)>`，但是根命名空間名稱的項目卻是以底線 \(`_`\) 開頭。  
  
 程式設計的項目可以包含一個以上的底線，但若要符合 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 標準，則不能以底線開頭。  請參閱[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
 當您將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，可以將屬性的 `isCompliant` 參數設定為 `True` 或 `False`，表示符合標準或不符合標準。  這個參數沒有預設值，所以您必須提供預設值。  
  
 如果沒有將 <xref:System.CLSCompliantAttribute> 套用至項目，會被認為是不相容。  
  
 根據預設，這是一個警告訊息。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID：**BC40039  
  
### 若要更正這個錯誤  
  
-   如果需要符合 CLS 標準，請變更根命名空間，讓所有項目都不是以底線開頭。  
  
-   如果需要命名空間名稱保持不變，則從組件中移除 <xref:System.CLSCompliantAttribute>，或將它標示為 `<CLSCompliant(False)>`。  
  
## 請參閱  
 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [\/rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)   
 [應用程式頁面，專案設計工具 \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)   
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
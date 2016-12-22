---
title: "&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36550"
  - "vbc36550"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36550"
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

在 Visual Basic 中擴充資料型別的唯一方法，是在標準模組內定義擴充方法。  擴充方法可以是 `Sub` 程序或 `Function` 程序。  所有擴充方法都必須在 <xref:System.Runtime.CompilerServices?displayProperty=fullName> 命名空間 \(Namespace\) 中，以擴充屬性 \(Attribute\) `<Extension()>` 標記。  包含擴充方法的模組也可以用此方法進行標記。  其他的擴充屬性用法都無效。  
  
 **錯誤 ID**：BC36550  
  
### 若要更正這個錯誤  
  
-   移除擴充屬性。  
  
-   將擴充重新設計為方法，並在封入模組中加以定義。  
  
## 範例  
 下列範例會為 `String` 資料型別定義 `Print` 方法。  
  
```  
Imports StringUtility  
Imports System.Runtime.CompilerServices  
Namespace StringUtility  
    <Extension()>   
    Module StringExtensions  
        <Extension()>   
        Public Sub Print (ByVal str As String)  
            Console.WriteLine(str)  
        End Sub  
    End Module  
End Namespace  
  
```  
  
## 請參閱  
 [屬性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [擴充方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)
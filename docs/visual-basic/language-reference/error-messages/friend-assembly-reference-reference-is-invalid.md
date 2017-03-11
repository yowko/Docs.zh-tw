---
title: "Friend assembly reference &lt;reference&gt; is invalid | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc31535"
  - "bc31535"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31535"
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 5
---
# Friend assembly reference &lt;reference&gt; is invalid
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Friend 組件參考 \<reference\> 無效以強式名稱簽署的組件必須在其 InternalsVisibleTo 宣告中指定公開金鑰。  
  
 傳遞至 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性建構函式的組件名稱識別出強式名稱組件，但不含 `PublicKey` 屬性。  
  
 **錯誤 ID**：BC31535  
  
### 若要更正這個錯誤  
  
1.  判斷強式名稱 friend 組件的公開金鑰。  使用 `PublicKey` 屬性加入公開金鑰，做為傳遞至 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性建構函式之組件名稱的一部分。  
  
## 請參閱  
 <xref:System.Reflection.AssemblyName>   
 [Friend 組件](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [如何：建立簽署的 Friend 組件](../Topic/How%20to:%20Create%20Signed%20Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)
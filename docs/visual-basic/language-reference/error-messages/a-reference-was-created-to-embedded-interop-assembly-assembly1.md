---
title: "A reference was created to embedded interop assembly &#39;&lt;assembly1&gt;&#39; because of an indirect reference to that assembly from assembly &#39;&lt;assembly2&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc40059"
  - "bc40059"
helpviewer_keywords: 
  - "VBC40059"
  - "BC40059"
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# A reference was created to embedded interop assembly &#39;&lt;assembly1&gt;&#39; because of an indirect reference to that assembly from assembly &#39;&lt;assembly2&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

已建立內嵌 Interop 組件 '\<assembly1\>' 的參考，因為該組件的間接參考來自組件 '\<assembly2\>'。請考慮變更其中任何一個組件上的 \[內嵌 Interop 型別\] 屬性。  
  
 您已加入組件 \(assembly1\) 的參考。這個組件的 `Embed Interop Types` 屬性已設定為 `True`，  這樣會指示編譯器內嵌該組件中的 Interop 型別資訊。  但是編譯器無法內嵌該組建中的 Interop 型別資訊，因為您所參考的另一個組件 \(assembly2\) 也在參考該組件 \(assembly1\)，而且其 `Embed Interop Types` 屬性已設定為 `False`。  
  
> [!NOTE]
>  將組件的 `Embed Interop Types` 屬性設定為 `True`，相當於使用命令列編譯器的 `/link` 選項。  
  
 **錯誤 ID**︰BC40059  
  
### 若要解決這個警告  
  
-   若要同時內嵌這兩個組件的 Interop 型別資訊，請將所有 assembly 1 參考上的 `Embed Interop Types` 屬性都設定為 `True`。  
  
-   若要移除警告，您可以將 assembly 1 的 `Embed Interop Types` 屬性設定為 `False`。  在此情況下，Interop 型別資訊會由主要 Interop 組件 \(PIA\) 提供。  
  
## 請參閱  
 [\/link](../../../visual-basic/reference/command-line-compiler/link.md)   
 [Programming with Primary Interop Assemblies](http://msdn.microsoft.com/zh-tw/306fa1d6-0703-4004-9e93-d0a57f1be81e)
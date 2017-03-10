---
title: "Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30961"
  - "bc30961"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30961"
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

'\<typename1\>' 型別的值無法轉換成 '\<typename2\>'。型別不相符的原因可能是因為混用了專案 '\<projectname1\>' 中的檔案參考 '\<filepath1\>' 和專案 '\<projectname2\>' 中的檔案參考 '\<filepath2\>'。如果這兩個組件是相同的，請嘗試替換這些參考，讓兩個參考都來自於相同位置。  
  
 在專案對組件 \(Assembly\) 具有多個檔案參考的情況下，編譯器 \(Compiler\) 無法保證可以將某個型別轉換成另一個型別。  
  
 每個檔案參考都會針對專案的輸出檔 \(通常是 DLL 檔\)，指定檔案路徑和名稱。  不過，編譯器無法保證輸出檔都來自相同的來源，或者它們都表示相同組件的相同版本。  因此，無法保證不同參考中的型別都是相同的型別，甚至無法保證可以將某個型別轉換成另一個型別。  
  
 如果您知道參考的組件具有相同的組件識別 \(Identity\)，就可以使用單一檔案參考。  「*組件識別*」\(Assembly Identity\) 會包括組件的名稱、版本、公開金鑰 \(Public Key\) \(如果有的話\)，以及文化特性 \(Culture\)。  此資訊可唯一識別組件。  
  
 **錯誤 ID︰**BC30961  
  
### 若要更正這個錯誤  
  
-   如果參考的組件具有相同的組件識別，則請移除或取代其中一個檔案參考，如此就只會有單一檔案參考。  
  
-   如果參考的組件沒有相同的組件識別，則請變更您的程式碼，如此它就不會嘗試將某個組件中的型別轉換成其他組件中的型別。  
  
## 請參閱  
 [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [管理專案中的參考](/visual-studio/ide/managing-references-in-a-project)   
 [如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
---
title: "&lt;訊息&gt; 這項錯誤也可能是因為混用了檔案參考和組件 &#39;&lt;assemblyname&gt;&#39; 的專案參考 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30971"
  - "vbc30971"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30971"
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &lt;訊息&gt; 這項錯誤也可能是因為混用了檔案參考和組件 &#39;&lt;assemblyname&gt;&#39; 的專案參考
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

\<訊息\> 這項錯誤也可能是因為混用了檔案參考和組件 '\<assemblyname\>' 的專案參考。 在上述情形中，請嘗試將專案 '\<projectname1\>' 中的檔案參考 '\<assemblyfilename\>' 以專案參考 '\<projectname2\>' 取代。  
  
 您專案中的程式碼會存取另一個專案的成員，但您的解決方案組態不允許 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器解析參考。  
  
 若要存取另一個組件中所定義的類型，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器必須有該組件的參考。 這必須是單一的明確參考，不會在專案之間造成循環參考。  
  
 **錯誤 ID︰**BC30971  
  
### 更正這個錯誤  
  
1.  決定哪些專案產生的最佳組件供專案參考。 這項決策可能會使用輕鬆存取檔案和更新頻率等準則。  
  
2.  在專案屬性中，加入包含組件之專案的參考，此組件定義所使用的類型。  
  
## 請參閱  
 [管理專案中的參考](/visual-studio/ide/managing-references-in-a-project)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [中斷參考的疑難排解](/visual-studio/ide/troubleshooting-broken-references)
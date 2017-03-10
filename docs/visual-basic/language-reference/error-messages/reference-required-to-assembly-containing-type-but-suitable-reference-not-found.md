---
title: "需要組件 &#39;&lt;assemblyidentity&gt;&#39; (包含類型 &#39;&lt;typename&gt;&#39;) 的參考，但是由於專案 &#39;&lt;projectname1&gt;&#39; 和 &#39;&lt;projectname2&gt;&#39; 之間模稜兩可，所以找不到適合的參考 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30969"
  - "vbc30969"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30969"
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# 需要組件 &#39;&lt;assemblyidentity&gt;&#39; (包含類型 &#39;&lt;typename&gt;&#39;) 的參考，但是由於專案 &#39;&lt;projectname1&gt;&#39; 和 &#39;&lt;projectname2&gt;&#39; 之間模稜兩可，所以找不到適合的參考
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

運算式使用專案外部定義的類型 \(例如類別、結構、介面、列舉或委派\)。 不過，專案參考超過一個定義其類型的組件。  
  
 上述專案會產生具有相同名稱的組件。 因此，編譯器無法判斷要針對您正在存取的類型使用哪個組件。  
  
 若要存取另一個組件中所定義的類型，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器必須有該組件的參考。 這必須是單一的明確參考，不會在專案之間造成循環參考。  
  
 **錯誤 ID︰**BC30969  
  
### 更正這個錯誤  
  
1.  決定哪些專案產生的最佳組件供專案參考。 這項決策可能會使用輕鬆存取檔案和更新頻率等準則。  
  
2.  在專案屬性中，加入包含組件之檔案的參考，而這個組件定義所使用的類型。  
  
## 請參閱  
 [管理專案中的參考](/visual-studio/ide/managing-references-in-a-project)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [中斷參考的疑難排解](/visual-studio/ide/troubleshooting-broken-references)
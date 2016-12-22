---
title: "Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; | Microsoft Docs"
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
  - "vbc30955"
  - "bc30955"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30955"
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

'\<typename1\>' 型別的值無法轉換成 '\<typename2\>'。型別不相符的原因可能是因為混用檔案參考和組件 '\<assemblyname\>' 的專案參考。請嘗試將專案 '\<projectname1\>' 中 '\<filepath\>' 的檔案參考取代成 '\<projectname2\>' 的專案參考。  
  
 在專案同時產生專案參考和檔案參考的情況下，編譯器 \(Compiler\) 無法保證可以將某個型別轉換成另一個型別。  
  
 下列虛擬程式碼說明會產生這個錯誤的情況。  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 專案 `P1` 會透過專案 `P2` 產生專案 `P3` 的間接專案參考，也會產生 `P3` 的直接檔案參考。  `commonObject` 的宣告使用 `P3` 的檔案參考，而 `P2.getCommonClass` 的呼叫使用 `P3` 的專案參考。  
  
 這種情況的問題是檔案參考指定 `P3` 之輸出檔的檔案路徑和名稱 \(一般是 p3.dll\)，而專案參考則是依專案名稱來識別來源專案 \(`P3`\)。  因為這個原因，所以編譯器無法保證透過這兩個不同的參考，型別 `P3.commonClass` 還是來自相同原始程式碼。  
  
 一般是在混合使用專案參考和檔案參考時，才會發生此情況。  在前一個說明中，如果 `P1` 產生 `P3` 的直接專案參考，而不是檔案參考，就不會發生這個問題。  
  
 **錯誤 ID：**BC30955  
  
### 若要更正這個錯誤  
  
-   將檔案參考變更為專案參考。  
  
## 請參閱  
 [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [管理專案中的參考](/visual-studio/ide/managing-references-in-a-project)   
 [如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
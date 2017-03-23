---
title: "滑鼠不存在 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrMouse_NoMouseIsPresent"
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# 滑鼠不存在
已呼叫 `My.Computer.Mouse` 物件的其中一個屬性，但是電腦未安裝滑鼠或滑鼠連接埠。  
  
### 更正這個錯誤  
  
-   在 `My.Computer.Mouse` 物件的屬性呼叫周圍加入 `Try...Catch` 區塊。  
  
     — 或 —  
  
-   在電腦上安裝滑鼠。  
  
## 請參閱  
 [My.Computer.Mouse Object](../../visual-basic/language-reference/objects/my-computer-mouse-object.md)   
 [Visual Basic 中的例外狀況和錯誤處理](http://msdn.microsoft.com/zh-tw/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Try...Catch...Finally Statement](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
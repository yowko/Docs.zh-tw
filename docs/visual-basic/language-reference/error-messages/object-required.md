---
title: "Object required (Visual Basic) | Microsoft Docs"
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
  - "vbrID424"
dev_langs: 
  - "VB"
ms.assetid: afdc660b-81a5-4c92-ac7e-9c3a3105fc16
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Object required (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

屬性 \(Property\) 和方法的參考通常需要一個明確的物件限定詞 \(Qualifier\)，  在此情況下便是如此。  
  
### 若要更正這個錯誤  
  
1.  請檢查物件屬性或方法的參考是否具有有效的物件限定詞。  如果您並未提供物件限定詞，請指定一個。  
  
2.  請檢查物件限定詞的拼字是否正確，並確認該物件在所參考的程式中為可見的部分。  
  
3.  如果已為主應用程式 \(Host Application\) 的 \[**開啟舊檔**\] 命令提供路徑，請檢查其中的引數是否正確。  
  
4.  請查閱物件的說明文件並確認這個動作是有效的。  
  
## 請參閱  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)
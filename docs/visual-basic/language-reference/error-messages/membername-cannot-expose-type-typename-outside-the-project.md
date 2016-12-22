---
title: "&#39;&lt;membername&gt;&#39; cannot expose type &#39;&lt;typename&gt;&#39; outside the project through &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39; | Microsoft Docs"
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
  - "bc30909"
  - "vbc30909"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30909"
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;membername&gt;&#39; cannot expose type &#39;&lt;typename&gt;&#39; outside the project through &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

變數、程序參數或函式傳回會公開 \(Expose\) 在容器 \(Container\) 外，但是已宣告為不可公開在容器外的型別。  
  
 下列基本架構程式碼會顯示產生這個錯誤的情況。  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 將型別宣告為 `Protected`、`Friend`、`Protected Friend` 或 `Private` 的用意是限制從宣告內容外的存取。  將它當做不嚴格限制存取之變數的資料型別，將失去原本的用意。  在上述基本架構程式碼中，將 `exposedVar` 設為 `Public` 會將 `privateClass` 公開給不應該存取它的程式碼。  
  
 **錯誤 ID：**BC30909  
  
### 若要更正這個錯誤  
  
-   將變數、程序參數或函數傳回的存取層級變更為至少和資料型別的存取層級一樣嚴格。  
  
## 請參閱  
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
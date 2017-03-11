---
title: "Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30369"
  - "bc30369"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Shared"
  - "BC30369"
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

您嘗試從共用程序內參考類別的非共用成員。  下列範例即顯示這類情況。  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 在前面的範例中，指派陳述式 \(Assignment Statement\) `x = 10` 會產生這個錯誤訊息。  這是因為共用程序正嘗試存取執行個體變數 \(Instance Variable\)。  
  
 變數 `x` 是執行個體成員，因為並未將該變數宣告為 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)。  類別 `sample` 的每一個執行個體都包含其個別變數 `x`。  當某個執行個體設定或變更 `x` 的值時，並不會影響其他任何執行個體中 `x` 的值。  
  
 不過，`setX` 程序在 `sample` 類別的所有執行個體之間為 `Shared`。  這表示，該程序與類別的任何一個執行個體都不相關，而是獨立於各執行個體執行操作。  由於未與特定執行個體連接，因此 `setX` 無法存取執行個體變數。  該程序只能在 `Shared` 變數上操作。  當 `setX` 設定或變更共用變數的值時，新的值會提供給類別的所有執行個體使用。  
  
 **錯誤 ID︰**BC30369  
  
### 若要更正這個錯誤  
  
1.  請決定要在類別的所有執行個體之間共用成員，或每一個執行個體各有一個成員。  
  
2.  如果您要在所有執行個體之間共用單獨一個成員，請將 `Shared` 關鍵字加入至成員宣告中。  請在程序宣告中保留 `Shared` 關鍵字。  
  
3.  如果您要讓每一個執行個體各自擁有自己的成員，則不要為成員宣告指定 `Shared`。  請移除程序宣告中的 `Shared` 關鍵字。  
  
## 請參閱  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
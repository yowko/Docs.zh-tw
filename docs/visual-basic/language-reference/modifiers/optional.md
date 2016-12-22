---
title: "Optional (Visual Basic) | Microsoft Docs"
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
  - "vb.Optional"
  - "vb.optional"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Optional keyword, contexts"
  - "Optional keyword"
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Optional (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定當呼叫程序時，可以省略程序引數。  
  
## 備註  
 每個選擇性參數，您必須指定為該參數的預設值的常數運算式。  如果運算式計算為[不](../../../visual-basic/language-reference/nothing.md)，預設值的數值資料型別作為參數的預設值。  
  
 如果參數清單包含選擇性的參數，其後的每一個參數必須是選擇性的。  
  
 `Optional` 修飾詞可用於以下內容中：  
  
-   [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  在呼叫的程序，不論有選擇性參數，您可以依位置或名稱傳遞引數。  如需詳細資訊，請參閱 [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)。  
  
> [!NOTE]
>  您也可以使用多載，以定義選擇性參數的程序。  如果您有一個選擇性參數，您可以定義兩個多載的版本的程序，一個接受參數，另一個則不會。  如需詳細資訊，請參閱 [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)。  
  
## 範例  
 下列範例會定義具有選擇性參數的程序。  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## 範例  
 下列範例會示範如何依位置傳遞引數，並依名稱傳遞引數呼叫程序。  程序有兩個選擇性參數。  
  
 [!CODE [VbVbalrKeywords#21](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrKeywords#21)]  
  
## 請參閱  
 [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)   
 [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [關鍵字](../../../visual-basic/reference/command-line-compiler/index.md)
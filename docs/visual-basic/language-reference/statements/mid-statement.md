---
title: "Mid Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.MidB"
  - "vb.Mid"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "substrings, Mid statement"
  - "strings [Visual Basic], substrings"
  - "Mid statement"
  - "strings [Visual Basic], replacing"
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Mid Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

用另一字串的字元來取代 `String` 變數中指定數量的字元。  
  
## 語法  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## 組件  
 `Target`  
 必要項。  所要修改的 `String` 變數名稱。  
  
 `Start`  
 必要項。  `Integer` 運算式。  `Target` 中的字元位置，取代文字的開始處。  `Start` 使用以一為基底的索引。  
  
 `Length`  
 選擇項。  `Integer` 運算式。  要取代的字元長度。  如果省略，則使用所有的 `String`。  
  
 `StringExpression`  
 必要項。  取代 `Target` 之部分的 `String` 運算式。  
  
## 例外狀況  
  
|例外狀況類型|條件|  
|------------|--------|  
|<xref:System.ArgumentException>|`Start` \<\= 0 或 `Length` \< 0。|  
  
## 備註  
 取代的字元數一律會小於或等於 `Target` 中的字元數。  
  
 Visual Basic 具有 <xref:Microsoft.VisualBasic.Strings.Mid%2A> 函式和 `Mid` 陳述式 \(Statement\)。  這些項目都會在字串內指定數目的字元上運作，但是 `Mid` 函式會傳回字元，而 `Mid` 陳述式則是會取代字元。  如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Strings.Mid%2A>。  
  
> [!NOTE]
>  在舊版的 Visual Basic 中，`MidB` 陳述式會以位元組為單位來取代子字串，而不是字元。  這項功能主要用來轉換雙位元組字元集 \(DBCS\) 應用程式中的字串。  所有的 Visual Basic 字串都是 Unicode，而且不再支援 `MidB`。  
  
## 範例  
 這個範例會使用 `Mid` 陳述式，以用另一個字串的字元來取代字串變數中指定數量的字元。  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## 需求  
 **命名空間**：[Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **模組**︰`Strings`  
  
 **組件** \(Assembly\)：[!INCLUDE[vbprvbruntime](../../../visual-basic/language-reference/objects/includes/vbprvbruntime-md.md)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>   
 [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md)   
 [Introduction to Strings in Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
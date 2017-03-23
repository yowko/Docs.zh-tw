---
title: "有效率地使用資料類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function, preferred to Asc
- data types [Visual Basic], using efficiently
- optimization, data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function, preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b81a1c81d970beee32925c3f2fe6ca3bcad79151
ms.lasthandoff: 03/13/2017

---
# <a name="efficient-use-of-data-types-visual-basic"></a>有效率地使用資料類型 (Visual Basic)
未宣告的變數和不具資料型別宣告的變數指派`Object`資料型別。 這樣可以容易撰寫的程式速度快，但它可能會使程式執行速度變慢。  
  
## <a name="strong-typing"></a>強型別  
 指定所有變數的資料型別稱為*強型別*。 使用強型別有下列優點︰  
  
-   它可讓您的變數的 IntelliSense 支援。 這可讓您查看其屬性和其他成員，當您輸入程式碼中。  
  
-   它會利用編譯器型別檢查。 這會攔截可能會在執行階段，因為例如溢位錯誤而失敗的陳述式。 也會對方法的呼叫攔截並不支援的物件。  
  
-   這樣可以更快地執行您的程式碼。  
  
## <a name="most-efficient-data-types"></a>最有效率的資料類型  
 對於絕對不能包含分數的變數，整數類資料類型會比非整數類型有效。 在[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，`Integer`和`UInteger`是最有效率的數字類型。  
  
 小數的數字，`Double`是最有效率的資料類型，因為目前平台上的處理器執行雙精度浮點數運算。 不過，作業`Double`速度與整數類資料型別，例如`Integer`。  
  
## <a name="specifying-data-type"></a>指定資料型別  
 使用[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)宣告特定型別的變數。 您可以使用，以同時指定其存取層級[公用](../../../../visual-basic/language-reference/modifiers/public.md)，[受保護](../../../../visual-basic/language-reference/modifiers/protected.md)， [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)，或[私人](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字，如下列範例所示。  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a>字元轉換  
 `AscW`和`ChrW`函式會以 Unicode 作業。 您應該使用這些優先`Asc`和`Chr`，這必須在傳入和傳出 Unicode 轉譯。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A></xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A></xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 <xref:Microsoft.VisualBasic.Strings.Chr%2A></xref:Microsoft.VisualBasic.Strings.Chr%2A>   
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A></xref:Microsoft.VisualBasic.Strings.ChrW%2A>   
 [資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [數值資料類型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)   
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [使用 IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense)

---
title: 有效率地使用資料類型 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4cac585cdc3072d595d2446e1937678f9ab03335
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="efficient-use-of-data-types-visual-basic"></a>有效率地使用資料類型 (Visual Basic)
指派給未宣告的變數和變數宣告為不具有資料類型的`Object`資料型別。 這樣可以輕鬆撰寫程式快速，但是它可能會使程式執行速度變慢。  
  
## <a name="strong-typing"></a>強型別  
 指定所有變數的資料型別稱為*強型別*。 使用強型別有多項優點：  
  
-   它可讓您的變數的 IntelliSense 支援。 這可讓您查看其屬性和其他成員，當您輸入程式碼中。  
  
-   它會利用的編譯器型別檢查。 這會攔截可能會在執行階段因為例如溢位錯誤而失敗的陳述式。 它也會對方法的呼叫攔截不支援它們的物件。  
  
-   這樣可以更快地執行您的程式碼。  
  
## <a name="most-efficient-data-types"></a>最有效率的資料類型  
 對於絕對不能包含分數的變數，整數類資料類型會更有效率的非整數類型。 在 Visual Basic 中`Integer`和`UInteger`是最有效率的數字類型。  
  
 小數點的數字，如`Double`是最有效率的資料類型，因為在目前的平台上的處理器執行雙精度浮點數運算。 不過，作業`Double`速度與整數類資料類型，例如`Integer`。  
  
## <a name="specifying-data-type"></a>指定資料類型  
 使用[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)宣告特定類型的變數。 您可以使用，以同時指定其存取層級[公用](../../../../visual-basic/language-reference/modifiers/public.md)，[保護](../../../../visual-basic/language-reference/modifiers/protected.md)， [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)，或[私人](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字，如下所示下列範例。  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a>字元轉換  
 `AscW`和`ChrW`函式會以 Unicode 作業。 您應該使用這些優先`Asc`和`Chr`，Unicode 進出，必須將其轉譯。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [數值資料類型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [使用 IntelliSense](/visualstudio/ide/using-intellisense)

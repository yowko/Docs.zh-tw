---
title: "如何︰ 建立新的變數 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Dim statement
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 2856fe19ddc48a14385aaae7b1c331fcb96c0554
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-new-variable-visual-basic"></a>如何：建立新的變數 (Visual Basic)
您建立的變數[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
### <a name="to-create-a-new-variable"></a>若要建立新變數  
  
1.  中宣告變數`Dim`陳述式。  
  
    ```  
  
    Dim newCustomer  
    ```  
  
2.  包含變數的特性的規格，例如[私用](../../../../visual-basic/language-reference/modifiers/private.md)，[靜態](../../../../visual-basic/language-reference/modifiers/static.md)，[陰影](../../../../visual-basic/language-reference/modifiers/shadows.md)，或[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)。 如需詳細資訊，請參閱[宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)。  
  
    ```  
    Public Static newCustomer  
    ```  
  
     您不需要`Dim`關鍵字宣告中使用其他關鍵字。  
  
3.  規格之後加上變數名稱，必須遵循[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]規則和慣例。 如需詳細資訊，請參閱[宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  在名稱後面加[為](../../../../visual-basic/language-reference/statements/as-clause.md)子句來指定變數的資料型別。  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     如果未指定資料型別，它會使用預設值︰ `Object`。  
  
5.  請依照下列`As`子句以等號 (`=`) 和變數的初始值為等號後面。  
  
     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]將指定的值指派給變數，每次執行`Dim`陳述式。 如果您未指定一個初始值，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會先進入包含的程式碼時，變數的資料型別預設初始值`Dim`陳述式。  
  
     如果變數是參考型別，您可以建立其類別的執行個體包括[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字`As`子句。 如果您不使用`New`，變數的初始值會是[Nothing](../../../../visual-basic/language-reference/nothing.md)。  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [變數](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [實值型別和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [陳述式](../../../../visual-basic/language-reference/statements/index.md)   
 [區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)

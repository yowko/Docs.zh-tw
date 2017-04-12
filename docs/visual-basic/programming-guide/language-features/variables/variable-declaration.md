---
title: "在 Visual Basic 中的變數宣告 |Microsoft 文件"
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
- variables [Visual Basic], declaring
- member variables, declarations
- Dim statement, variable declaration
- declaring variables
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime, variables
- variables [Visual Basic], lifetime
- access levels, variables
- scope, declaration statements
- variables [Visual Basic], access level
- local variables, declarations
- scope, variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
caps.latest.revision: 31
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8cabb2d319288653c80099c816e46e822429d6ec
ms.lasthandoff: 03/13/2017

---
# <a name="variable-declaration-in-visual-basic"></a>Visual Basic 中的變數宣告
您宣告變數，以指定其名稱和特性。 變數的宣告陳述式是[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)。 其位置及內容會決定變數的特性。  
  
 變數的命名規則及考量，請參閱[宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
## <a name="declaration-levels"></a>宣告層級  
  
### <a name="local-and-member-variables"></a>本機和成員變數  
 A*區域變數*是其中一個程序內宣告。 A*成員變數*隸屬[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]輸入; 它在模組層級，在類別、 結構或模組，但不是在任何程序內部的類別、 結構或模組內宣告。  
  
### <a name="shared-and-instance-variables"></a>共用與執行個體變數  
 在類別或結構中，成員變數的類別取決於共用。 如果它以宣告[共用](../../../../visual-basic/language-reference/modifiers/shared.md)關鍵字，它是*共用的變數*，並且存在於類別或結構的所有執行個體之間共用的單一複本。  
  
 否則，它會*執行個體變數*，並為類別或結構的每個執行個體建立個別的複本。 指定的複本的執行個體變數是僅適用於類別或結構建立所在的執行個體。 它是複本的變數的獨立的執行個體中類別或結構的任何其他執行個體。  
  
## <a name="declaring-data-type"></a>宣告資料型別  
 [為](../../../../visual-basic/language-reference/statements/as-clause.md)子句中的宣告陳述式可讓您定義資料型別或物件類型所宣告的變數。 您可以指定任何下列類型的變數︰  
  
-   基本的資料類型，例如`Boolean`， `Long`，或`Decimal`  
  
-   複合資料類型，例如陣列或結構  
  
-   物件類型或類別，定義您的應用程式或其他應用程式  
  
-   A[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]類別，例如<xref:System.Windows.Forms.Label>或<xref:System.Windows.Forms.TextBox></xref:System.Windows.Forms.TextBox></xref:System.Windows.Forms.Label>  
  
-   介面類型，例如<xref:System.IComparable>或<xref:System.IDisposable></xref:System.IDisposable></xref:System.IComparable>  
  
 您可以宣告一個陳述式中的數個變數而不用重複的資料型別。 下列陳述式的變數`i`， `j`，和`k`宣告為類型`Integer`，`l`和`m`為`Long`，和`x`和`y`為`Single`:  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 如需有關資料類型的詳細資訊，請參閱[資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md)。 如需有關物件的詳細資訊，請參閱[物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)和[元件程式設計](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)。  
  
## <a name="local-type-inference"></a>區域類型推斷  
 *型別推斷*用來判斷資料類型的未宣告的區域變數`As`子句。 編譯器會推斷變數的初始化運算式的型別類型。 這可讓您宣告變數而不用明確陳述型別。 在下列範例中，同時`num1`和`num2`強型別為整數。  
  
 [!code-vb[VbVbalrTypeInference #&1;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]  
  
 如果您想要使用區域型別推斷`Option Infer`必須設為`On`。 如需詳細資訊，請參閱[本機的型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)和[Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。  
  
## <a name="characteristics-of-declared-variables"></a>宣告變數的特性  
 *存留期*的變數是一段時間期間它是可供使用。 一般情況下，變數存在，只要宣告 （例如程序或類別） 的項目會繼續存在。 如果變數不需要其包含項目的存留期過後繼續存在，您不需要任何特別的宣告中。 如果變數需要持續時間超過其包含項目存在，您可以包含`Static`或`Shared`關鍵字其`Dim`陳述式。 如需詳細資訊，請參閱[在 Visual Basic 中的存留期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)。  
  
 *範圍*變數是完全不需限定其名稱參考的所有程式碼。 變數的範圍取決於宣告的位置。 位於指定區域中的程式碼可以使用定義於該區域中，而不需要完整名稱的變數。 如需詳細資訊，請參閱[Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)。  
  
 變數的*存取層級*是具有存取權限的程式碼的範圍。 這取決於存取修飾詞 (例如[公用](../../../../visual-basic/language-reference/modifiers/public.md)或[私用](../../../../visual-basic/language-reference/modifiers/private.md)) 中使用`Dim`陳述式。 如需詳細資訊，請參閱[在 Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何︰ 建立新的變數](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)   
 [如何︰ 移入和移出變數資料](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)   
 [資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [受保護](../../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)   
 [靜態](../../../../visual-basic/language-reference/modifiers/static.md)   
 [宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)

---
title: HOW TO：宣告物件使用物件初始設定式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: e0673c9faceb3bd9fc71123a2ae22abbc7061c04
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970203"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>HOW TO：宣告物件使用物件初始設定式 (Visual Basic)
物件初始設定式可讓您宣告並具現化類別，以單一陳述式的執行個體。 此外，您可以在此同時，初始化執行個體的一或多個成員，而不叫用的參數化建構函式。  
  
 當您使用物件初始設定式來建立具名型別的執行個體時，會呼叫類別預設建構函式，後面接著初始化指定的成員，您所指定的順序。  
  
 下列程序示範如何建立的執行個體`Student`方式有三種類別。 此類別具有名字、 姓氏和年級屬性等等。 三個宣告的每個建立的新執行個體`Student`，具有屬性`First`設定為"Michael，"屬性`Last`設定為"Tucker"，而所有其他成員設定為其預設值。 在程序中的每個宣告的結果就相當於下列範例中，不會使用物件初始設定式項目。  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 如需實作的`Student`類別，請參閱[How to:建立項目清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)。 您可以複製設定的類別，並建立一份該主題中的程式碼`Student`可用的物件。  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>若要使用物件初始設定式建立具名類別的物件  
  
1.  如果您打算使用建構函式，請開始宣告。  
  
     `Dim student1 As New Student`  
  
2.  輸入關鍵字`With`，後面接著括號括住的初始化清單。  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  在初始設定清單中，包含每個您想要初始化，並將初始值指派給它的屬性。 屬性的名稱前面有一個句號。  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     您可以初始化類別的一或多個成員。  
  
4.  或者，您可以宣告類別的新執行個體，並再將值指派給它。 首先，宣告的執行個體`Student`:  
  
     `Dim student2 As Student`  
  
5.  開始建立的執行個體`Student`以一般方式。  
  
     `Dim student2 As Student = New Student`  
  
6.  型別`With`，然後物件初始設定式來初始化新執行個體的一或多個成員。  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7.  您可以簡化在上一個步驟中的定義，藉由略過`As Student`。 如果您這麼做時，編譯器會判斷所`student3`的執行個體`Student`使用區域型別推斷。  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     如需詳細資訊，請參閱 <<c0> [ 區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
## <a name="see-also"></a>另請參閱
- [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [如何：建立項目清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [物件初始設定式：具名和匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)

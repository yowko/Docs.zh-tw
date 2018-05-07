---
title: 如何：使用物件初始設定式宣告物件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: 3a372ba91377b53c87c05976e416ca8ed55ccbbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>如何：使用物件初始設定式宣告物件 (Visual Basic)
物件初始設定式可讓您宣告並具現化類別，以在單一陳述式的執行個體。 此外，您可以在相同的時間初始化執行個體的一或多個的成員，而不叫用的參數化建構函式。  
  
 當您使用物件初始設定式來建立具名型別的執行個體時，會呼叫類別的預設建構函式，後面接著初始化指定的成員，您所指定的順序。  
  
 下列程序示範如何建立執行個體`Student`三種不同方式的類別。 類別有名字、 姓氏和年級屬性和其他項目。 每三個宣告建立的新執行個體`Student`，與屬性`First`設為"Michael，"屬性`Last`設定為"Tucker"，而所有其他成員設定為其預設值。 程序中的每個宣告的結果就相當於下列的範例中，不會使用物件初始設定式。  
  
 [!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]  
  
 實作`Student`類別，請參閱[How to： 建立項目的清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)。 您可以從設定的類別，並建立一份該主題複製程式碼`Student`若要使用的物件。  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>若要使用物件初始設定式建立具名類別的物件  
  
1.  開始宣告，如同您計劃使用建構函式。  
  
     `Dim student1 As New Student`  
  
2.  輸入關鍵字`With`，後面接著括號括住的初始設定清單。  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  在初始設定清單中，包含您想要初始化，並將初始值指派給它的每一個屬性。 屬性名稱前面有一個句號。  
  
     [!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]  
  
     您可以初始化類別的一個或多個成員。  
  
4.  或者，您可以宣告類別的新執行個體，然後再將值指派給它。 首先，宣告的執行個體`Student`:  
  
     `Dim student2 As Student`  
  
5.  開始的執行個體建立`Student`以一般方式。  
  
     `Dim student2 As Student = New Student`  
  
6.  型別`With`，然後物件初始設定式來初始化新執行個體的一或多個成員。  
  
     [!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]  
  
7.  您可以藉由略過簡化上一個步驟中的定義`As Student`。 如果您這樣做，在編譯器判斷`student3`的執行個體`Student`使用區域類型推斷。  
  
     [!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]  
  
     如需詳細資訊，請參閱[區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
## <a name="see-also"></a>另請參閱  
 [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [如何：建立項目清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)  
 [物件初始設定式：具名和匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)

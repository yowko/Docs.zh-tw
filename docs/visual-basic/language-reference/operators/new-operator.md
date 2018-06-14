---
title: New 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
ms.openlocfilehash: 0fe511b2c16681d7bab7eeda7c121fcbbaa2f5dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603635"
---
# <a name="new-operator-visual-basic"></a>New 運算子 (Visual Basic)
導入了`New`子句來建立新的物件執行個體，指定型別參數的建構函式條件約束，或識別`Sub`與類別建構函式的程序。  
  
## <a name="remarks"></a>備註  
 在宣告或指派陳述式，`New`子句必須指定已定義的類別，可以從中建立執行個體。 這表示類別必須公開一個或多個建構函式呼叫的程式碼可以存取。  
  
 您可以使用`New`宣告陳述式或指派陳述式中的子句。 陳述式執行時，它會呼叫適當的建構函式指定類別，並傳遞您提供任何引數。 下列範例會示範這藉由建立的執行個體`Customer`類別具有兩個建構函式不接受參數，一個可接受字串參數。  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 由於陣列是類別，`New`可以建立新的陣列執行個體，如下列範例所示。  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 Common language runtime (CLR) 擲回<xref:System.OutOfMemoryException>如果記憶體不足，無法建立新的執行個體的錯誤。  
  
> [!NOTE]
>  `New`關鍵字也用在型別參數清單來指定提供的型別必須公開存取的無參數建構函式。 如需型別參數和條件約束的詳細資訊，請參閱[型別清單](../../../visual-basic/language-reference/statements/type-list.md)。  
  
 若要建立之類別的建構函式程序，將名稱設定`Sub`程序`New`關鍵字。 如需詳細資訊，請參閱[物件存留期： 物件的建立和終結](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。  
  
 `New` 關鍵字可用於以下內容：  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.OutOfMemoryException>  
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)  
 [類型清單](../../../visual-basic/language-reference/statements/type-list.md)  
 [Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [物件存留期：物件的建立和終結](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)

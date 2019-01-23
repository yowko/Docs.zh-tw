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
ms.openlocfilehash: 0e8ec5877cba5f5cf97e1677460da06fd87cce1c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587550"
---
# <a name="new-operator-visual-basic"></a>New 運算子 (Visual Basic)
導入了`New`子句，以建立新的物件執行個體，指定型別參數的建構函式條件約束，或識別`Sub`類別建構函式與程序。  
  
## <a name="remarks"></a>備註  
 在宣告或指派陳述式，`New`子句必須指定已定義的類別，可以從中建立執行個體。 這表示此類別必須公開一或多個建構函式呼叫的程式碼可以存取。  
  
 您可以使用`New`宣告陳述式或指派陳述式中的子句。 陳述式執行時，它會呼叫指定的類別，將您提供任何引數傳遞的適當建構函式。 下列範例所示範的是這所建立的執行個體`Customer`有兩個建構函式的類別，其中一個不接受任何參數，另一個會採用字串參數。  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 由於陣列是類別，`New`可以建立新的陣列執行個體，如下列範例所示。  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 Common language runtime (CLR) 會擲回<xref:System.OutOfMemoryException>錯誤，如果沒有記憶體不足，無法建立新的執行個體。  
  
> [!NOTE]
>  `New`關鍵字也用在類型參數清單中，指定提供的型別必須公開存取的無參數建構函式。 如需有關型別參數和條件約束的詳細資訊，請參閱[型別清單](../../../visual-basic/language-reference/statements/type-list.md)。  
  
 若要建立類別的建構函式程序，將名稱設定`Sub`程序`New`關鍵字。 如需詳細資訊，請參閱[物件存留期：如何建立和終結物件](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。  
  
 `New` 關鍵字可用於以下內容：  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱
- <xref:System.OutOfMemoryException>
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
- [類型清單](../../../visual-basic/language-reference/statements/type-list.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [物件存留期：如何建立和終結物件](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)

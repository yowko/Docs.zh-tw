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
ms.openlocfilehash: 36cf71529b1f81c27881638d788117222c37171d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955872"
---
# <a name="new-operator-visual-basic"></a>New 運算子 (Visual Basic)
引進子句來建立新的物件實例、在型別參數上指定一個函式條件約束, 或`Sub`將程式識別為類別的方法。 `New`  
  
## <a name="remarks"></a>備註  
 在宣告或指派語句中, `New`子句必須指定可從中建立實例的已定義類別。 這表示類別必須公開呼叫程式碼可以存取的一個或多個函式。  
  
 您可以在宣告`New`語句或指派語句中使用子句。 當語句執行時, 它會呼叫指定類別的適當的函式, 並傳遞您所提供的任何引數。 下列範例會藉由建立具有兩個函`Customer`式的類別實例 (不接受任何參數, 另一個採用字串參數) 來示範。  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 由於陣列是類別, `New`因此可以建立新的陣列實例, 如下列範例所示。  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 如果記憶體不足, 無法建立新的實例<xref:System.OutOfMemoryException> , 則 common language runtime (CLR) 會擲回錯誤。  
  
> [!NOTE]
> `New`關鍵字也會用於型別參數清單中, 以指定提供的型別必須公開可存取的無參數函數。 如需型別參數和條件約束的詳細資訊, 請參閱[Type List](../../../visual-basic/language-reference/statements/type-list.md)。  
  
 若要建立類別的`Sub`方法, 請將程式的名稱設定`New`為關鍵字。 如需詳細資訊, [請參閱物件存留期:如何建立和](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)終結物件。  
  
 `New` 關鍵字可用於以下內容：  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱

- <xref:System.OutOfMemoryException>
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
- [類型清單](../../../visual-basic/language-reference/statements/type-list.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [物件存留期:物件的建立和終結方式](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)

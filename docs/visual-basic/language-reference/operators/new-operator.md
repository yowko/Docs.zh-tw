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
ms.openlocfilehash: c0870f4b056658a22928769c369024cdda24f354
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799045"
---
# <a name="new-operator-visual-basic"></a>New 運算子 (Visual Basic)

引進了一個 `New` 子句來建立新的物件實例、在型別參數上指定一個函式條件約束，或將 `Sub` 的程式識別為類別的函式。

## <a name="remarks"></a>備註

在宣告或指派語句中，`New` 子句必須指定可從中建立實例的已定義類別。 這表示類別必須公開呼叫程式碼可以存取的一個或多個函式。

您可以在宣告語句或指派語句中使用 `New` 子句。 當語句執行時，它會呼叫指定類別的適當的函式，並傳遞您所提供的任何引數。 下列範例會藉由建立具有兩個函式的 `Customer` 類別實例（其中一個不接受參數，另一個採用字串參數）來示範：

[!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]

由於陣列是類別，因此 `New` 可以建立新的陣列實例，如下列範例所示：

[!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]

如果記憶體不足，無法建立新的實例，則 common language runtime （CLR）會擲回 <xref:System.OutOfMemoryException> 錯誤。

> [!NOTE]
> `New` 關鍵字也會用於型別參數清單中，以指定提供的型別必須公開可存取的無參數函數。 如需型別參數和條件約束的詳細資訊，請參閱[Type List](../statements/type-list.md)。

若要建立類別的函式程式，請將 `Sub` 程式的名稱設定為 `New` 關鍵字。 如需詳細資訊，請參閱[物件存留期：物件的建立和終結方式](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。

`New` 關鍵字可用於以下內容：

- [Dim 陳述式](../statements/dim-statement.md)
- [Of](../statements/of-clause.md)
- [Sub 陳述式](../statements/sub-statement.md)

## <a name="see-also"></a>請參閱

- <xref:System.OutOfMemoryException>
- [關鍵字](../keywords/index.md)
- [類型清單](../statements/type-list.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [物件存留期：物件的建立和終結](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)

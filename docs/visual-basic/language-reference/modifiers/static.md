---
title: Static (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: de4f67fc5b60de48383a8ca886cff02b03830318
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814165"
---
# <a name="static-visual-basic"></a>Static (Visual Basic)
指定一或多個宣告的區域變數會繼續存在，並在其宣告的程序終止之後保留最後的值。  
  
## <a name="remarks"></a>備註  
 一般來說，程序中的區域變數就不會存在，程序會停止。 靜態變數就會繼續存在，並保留其最新的值。 下次當您的程式碼呼叫程序中，不會重新初始化的變數，和它仍會保留最新的值指派給它。 靜態變數，就會繼續存在的存留期內的類別或模組中定義。  
  
## <a name="rules"></a>規則  
  
-   **宣告內容。** 您可以使用`Static`只對本機變數。 這表示的宣告內容`Static`變數必須程序或程序中的區塊，而且它不能是原始程式檔、 命名空間、 類別、 結構或模組。  
  
     您無法使用`Static`結構程序內。  
  
-   資料類型的`Static`無法推斷區域變數。 如需詳細資訊，請參閱 <<c0> [ 區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
-   **結合的修飾詞。** 您無法指定`Static`連同`ReadOnly`， `Shadows`，或`Shared`相同宣告中。  
  
## <a name="behavior"></a>行為  
 當您宣告中的靜態變數`Shared`程序的靜態變數只有一個複本是適用於整個應用程式。 您呼叫`Shared`使用類別的程序，不為變數命名，以指向類別的執行個體。  
  
 當您宣告靜態變數中的程序，不是`Shared`，只有一個變數的複本可供類別的每個執行個體。 您可以使用此變數會指向特定類別的執行個體，以呼叫非共用程序。  
  
## <a name="example"></a>範例  
 下列範例示範 `Static` 的用法。  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 `Static`變數`totalSales`會初始化為 0 僅一次。 您輸入每次`updateSales`，`totalSales`還有您計算的最新值。  
  
 `Static`修飾詞，請使用此內容中：  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [在 Visual Basic 中的存留期](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [變數宣告](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)

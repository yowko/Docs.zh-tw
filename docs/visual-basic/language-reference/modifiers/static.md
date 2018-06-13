---
title: Static (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 2cbd99a026a5ebf0e215ee5732d62ccf639d3836
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602050"
---
# <a name="static-visual-basic"></a>Static (Visual Basic)
指定一或多個宣告的區域變數會繼續存在，且在宣告的程序終止之後保持最新的值。  
  
## <a name="remarks"></a>備註  
 一般來說，程序中的區域變數就不會存在儘速程序會停止。 靜態變數會繼續存在，並會保留最新的值。 您的程式碼呼叫的程序，在下一次不會重新初始化變數，和它仍會保留您指派給它的最新值。 靜態變數會繼續存在的類別或模組中定義的存留期間。  
  
## <a name="rules"></a>規則  
  
-   **宣告內容。** 您可以使用`Static`只對本機變數。 這表示宣告內容`Static`變數必須在程序或程序中的區塊，而且不得原始程式檔、 命名空間、 類別、 結構或模組。  
  
     您無法使用`Static`結構程序內。  
  
-   資料類型的`Static`無法推斷本機變數。 如需詳細資訊，請參閱[區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
-   **結合的修飾詞。** 您無法指定`Static`搭配`ReadOnly`， `Shadows`，或`Shared`相同宣告中。  
  
## <a name="behavior"></a>行為  
 當您宣告中的靜態變數`Shared`程序只能有一個靜態變數的複本是適用於整個應用程式。 您呼叫`Shared`程序使用類別的名稱，不是變數，以指向類別的執行個體。  
  
 當您宣告靜態變數不是程序中的`Shared`，只有一個變數的複本可供每個執行個體的類別。 您可以使用的變數會指向特定類別的執行個體來呼叫非共用程序。  
  
## <a name="example"></a>範例  
 下列範例示範 `Static` 的用法。  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 `Static`變數`totalSales`會初始化為 0 僅一次。 您輸入每次`updateSales`，`totalSales`仍有最新您計算的值。  
  
 `Static`修飾詞可用於此內容：  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [在 Visual Basic 中的存留期](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [變數宣告](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)

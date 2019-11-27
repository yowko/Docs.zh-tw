---
title: Static
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: f020756466888f51298abb423997906ddc7caff7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350765"
---
# <a name="static-visual-basic"></a>Static (Visual Basic)
指定一個或多個宣告的區域變數要繼續存在，並在終止宣告它們的程式之後保留其最新值。  
  
## <a name="remarks"></a>備註  
 一般來說，程式停止時，程式中的區域變數就會停止存在。 靜態變數會繼續存在，並保留其最新的值。 下一次您的程式碼呼叫程式時，變數不會重新初始化，而且仍然會保留您指派給它的最新值。 靜態變數會繼續存在於其定義所在之類別或模組的存留期間。  
  
## <a name="rules"></a>規則  
  
- **宣告內容。** 您只能在本機變數上使用 `Static`。 這表示 `Static` 變數的宣告內容必須是程式或程式中的區塊，而且不能是原始程式檔、命名空間、類別、結構或模組。  
  
     您不能在結構程式中使用 `Static`。  
  
- 無法推斷 `Static` 本機變數的資料類型。 如需詳細資訊，請參閱[區欄位型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
- **合併的修飾詞。** 您不能在相同的宣告中同時指定 `Static` 與 `ReadOnly`、`Shadows`或 `Shared`。  
  
## <a name="behavior"></a>行為  
 當您在 `Shared` 程式中宣告靜態變數時，整個應用程式只能有一個靜態變數複本。 您可以使用類別名稱來呼叫 `Shared` 程式，而不是指向類別實例的變數。  
  
 當您在不 `Shared`的程式中宣告靜態變數時，類別的每個實例只能有一個變數複本。 您可以使用指向類別之特定實例的變數來呼叫非共用程式。  
  
## <a name="example"></a>範例  
 下列範例示範 `Static` 的用法。  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 `Static` 變數 `totalSales` 只會初始化為0一次。 每次您輸入 `updateSales`時，`totalSales` 仍會有您為它計算的最新值。  
  
 `Static` 修飾詞可以在此內容中使用：  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>請參閱

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [共用](../../../visual-basic/language-reference/modifiers/shared.md)
- [Visual Basic 中的存留期](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [變數宣告](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)

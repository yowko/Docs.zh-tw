---
title: 靜態
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 3b323d5fb1c4f1357b9f476213793c69d29b7208
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402690"
---
# <a name="static-visual-basic"></a>Static (Visual Basic)
指定一個或多個宣告的區域變數要繼續存在，並在終止宣告它們的程式之後保留其最新值。  
  
## <a name="remarks"></a>備註  
 一般來說，程式停止時，程式中的區域變數就會停止存在。 靜態變數會繼續存在，並保留其最新的值。 下一次您的程式碼呼叫程式時，變數不會重新初始化，而且仍然會保留您指派給它的最新值。 靜態變數會繼續存在於其定義所在之類別或模組的存留期間。  
  
## <a name="rules"></a>規則  
  
- **宣告內容。** 您 `Static` 只能在本機變數上使用。 這表示變數的宣告內容 `Static` 必須是程式或程式中的區塊，而且不能是原始程式檔、命名空間、類別、結構或模組。  
  
     您無法在 `Static` 結構程式內使用。  
  
- `Static`無法推斷本機變數的資料類型。 如需詳細資訊，請參閱[區欄位型別推斷](../../programming-guide/language-features/variables/local-type-inference.md)。  
  
- **結合的修飾詞。** 您不能 `Static` `ReadOnly` `Shadows` 在相同的宣告中，搭配、或來指定 `Shared` 。  
  
## <a name="behavior"></a>行為  
 當您在程式中宣告靜態變數時 `Shared` ，整個應用程式只能有一個靜態變數複本。 您可以 `Shared` 使用類別名稱呼叫程式，而不是指向類別實例的變數。  
  
 當您在不是的程式中宣告靜態變數時 `Shared` ，類別的每個實例只能有一個變數複本。 您可以使用指向類別之特定實例的變數來呼叫非共用程式。  
  
## <a name="example"></a>範例  
 下列範例示範 `Static` 的用法。  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 `Static`變數 `totalSales` 只會初始化為0一次。 每次您輸入時 `updateSales` ， `totalSales` 仍會有您為它計算的最新值。  
  
 `Static`修飾詞可以在此內容中使用：  
  
 [Dim 陳述式](../statements/dim-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [Shadows](shadows.md)
- [共用][](shared.md)
- [Visual Basic 中的存留期](../../programming-guide/language-features/declared-elements/lifetime.md)
- [變數宣告](../../programming-guide/language-features/variables/variable-declaration.md)
- [結構](../../programming-guide/language-features/data-types/structures.md)
- [區域型別推斷](../../programming-guide/language-features/variables/local-type-inference.md)
- [物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)

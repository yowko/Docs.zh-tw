---
title: 如何：建立集合初始設定式所使用的集合
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 5eaf9e828455bf2accda86ab52a1ce645f10b9ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349054"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>如何：建立集合初始設定式所使用的集合 (Visual Basic)
當您使用集合初始化運算式來建立集合時，Visual Basic 編譯器會搜尋集合類型的 `Add` 方法，其中 `Add` 方法的參數會符合集合初始化運算式中的數值型別。 這個 `Add` 方法是用來在集合中填入集合初始化運算式的值。  
  
## <a name="example"></a>範例  
 下列範例顯示 `OrderCollection` 集合，其中包含集合初始化運算式可用來加入 `Order`類型物件的公用 `Add` 方法。 `Add` 方法可讓您使用縮短的集合初始化運算式語法。  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>請參閱

- [集合初始設定式](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [如何：建立集合初始設定式所使用的 Add 擴充方法](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)

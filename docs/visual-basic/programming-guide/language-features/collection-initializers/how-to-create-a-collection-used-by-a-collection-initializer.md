---
title: 如何：建立集合初始設定式所使用的集合
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: b332ffb44ebc20ce8431e586fc380b8c6a29967d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086370"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>如何：建立集合初始設定式所使用的集合 (Visual Basic)

當您使用集合初始化運算式建立集合時，Visual Basic 編譯器會搜尋 `Add` 集合型別的方法，而該方法的參數與 `Add` 集合初始化運算式中的數值型別相符。 這個 `Add` 方法是用來在集合中填入集合初始化運算式中的值。  
  
## <a name="example"></a>範例  

 下列範例 `OrderCollection` 會顯示集合，其中包含 `Add` 集合初始化運算式可以用來加入型別物件的公用方法 `Order` 。 `Add`方法可讓您使用縮短的集合初始化運算式語法。  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [集合初始化運算式](index.md)
- [如何：建立集合初始設定式所使用的 Add 擴充方法](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)

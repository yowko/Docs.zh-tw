---
title: HOW TO：建立集合，使用集合初始設定式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: d0007ebf5f18dee5bd8448a071fe1f0f984aff1a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967447"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>HOW TO：建立集合，使用集合初始設定式 (Visual Basic)
當您使用集合初始設定式來建立集合時，Visual Basic 編譯器會搜尋`Add`的集合型別的方法的參數`Add`方法符合集合初始設定式中的值型別。 這`Add`方法用來擴展集合，集合初始設定式中的值。  
  
## <a name="example"></a>範例  
 下列範例所示`OrderCollection`集合，其中包含公用`Add`方法，可讓集合初始設定式加入物件的型別`Order`。 `Add`方法可讓您使用簡短的集合初始設定式語法。  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>另請參閱
- [集合初始設定式](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [如何：建立新增為集合初始設定式所使用的擴充方法](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)

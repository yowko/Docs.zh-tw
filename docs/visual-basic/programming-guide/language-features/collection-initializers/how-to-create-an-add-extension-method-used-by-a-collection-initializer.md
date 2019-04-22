---
title: HOW TO：建立 Add 擴充方法使用集合初始設定式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: a5af41e25b8f82aa173e2df28cc41b313c8d68dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825400"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>HOW TO：建立 Add 擴充方法使用集合初始設定式 (Visual Basic)
當您使用集合初始設定式來建立集合時，Visual Basic 編譯器會搜尋`Add`的集合型別的方法的參數`Add`方法符合集合初始設定式中的值型別。 這`Add`方法用來擴展集合，集合初始設定式中的值。  
  
 如果沒有相符`Add`方法存在，您無法修改集合的程式碼，您可以加入擴充方法呼叫`Add`採用所需的集合初始設定式的參數。 這通常是您需要您針對泛型集合使用集合初始設定式時執行的作業。  
  
## <a name="example"></a>範例  
 下列範例示範如何將擴充方法新增至泛型<xref:System.Collections.Generic.List%601>類型，讓集合初始設定式可以用來加入型別之物件`Employee`。 擴充方法可讓您使用簡短的集合初始設定式語法。  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [集合初始設定式](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [如何：建立集合，集合初始設定式使用](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)

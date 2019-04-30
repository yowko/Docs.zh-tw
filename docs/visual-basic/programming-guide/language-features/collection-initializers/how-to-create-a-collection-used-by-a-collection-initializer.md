---
title: HOW TO：建立集合，使用集合初始設定式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 75c280b57df03bde173c740123cccda278536dc1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053622"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="da530-102">HOW TO：建立集合，使用集合初始設定式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da530-102">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="da530-103">當您使用集合初始設定式來建立集合時，Visual Basic 編譯器會搜尋`Add`的集合型別的方法的參數`Add`方法符合集合初始設定式中的值型別。</span><span class="sxs-lookup"><span data-stu-id="da530-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="da530-104">這`Add`方法用來擴展集合，集合初始設定式中的值。</span><span class="sxs-lookup"><span data-stu-id="da530-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da530-105">範例</span><span class="sxs-lookup"><span data-stu-id="da530-105">Example</span></span>  
 <span data-ttu-id="da530-106">下列範例所示`OrderCollection`集合，其中包含公用`Add`方法，可讓集合初始設定式加入物件的型別`Order`。</span><span class="sxs-lookup"><span data-stu-id="da530-106">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="da530-107">`Add`方法可讓您使用簡短的集合初始設定式語法。</span><span class="sxs-lookup"><span data-stu-id="da530-107">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="da530-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da530-108">See also</span></span>

- [<span data-ttu-id="da530-109">集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="da530-109">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="da530-110">如何：建立新增為集合初始設定式所使用的擴充方法</span><span class="sxs-lookup"><span data-stu-id="da530-110">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)

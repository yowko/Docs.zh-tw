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
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="fa722-102">如何：建立集合初始設定式所使用的集合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa722-102">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>

<span data-ttu-id="fa722-103">當您使用集合初始化運算式建立集合時，Visual Basic 編譯器會搜尋 `Add` 集合型別的方法，而該方法的參數與 `Add` 集合初始化運算式中的數值型別相符。</span><span class="sxs-lookup"><span data-stu-id="fa722-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="fa722-104">這個 `Add` 方法是用來在集合中填入集合初始化運算式中的值。</span><span class="sxs-lookup"><span data-stu-id="fa722-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa722-105">範例</span><span class="sxs-lookup"><span data-stu-id="fa722-105">Example</span></span>  

 <span data-ttu-id="fa722-106">下列範例 `OrderCollection` 會顯示集合，其中包含 `Add` 集合初始化運算式可以用來加入型別物件的公用方法 `Order` 。</span><span class="sxs-lookup"><span data-stu-id="fa722-106">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="fa722-107">`Add`方法可讓您使用縮短的集合初始化運算式語法。</span><span class="sxs-lookup"><span data-stu-id="fa722-107">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="fa722-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa722-108">See also</span></span>

- [<span data-ttu-id="fa722-109">集合初始化運算式</span><span class="sxs-lookup"><span data-stu-id="fa722-109">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="fa722-110">如何：建立集合初始設定式所使用的 Add 擴充方法</span><span class="sxs-lookup"><span data-stu-id="fa722-110">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)

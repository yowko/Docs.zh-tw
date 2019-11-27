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
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="4ee4f-102">如何：建立集合初始設定式所使用的集合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ee4f-102">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="4ee4f-103">當您使用集合初始化運算式來建立集合時，Visual Basic 編譯器會搜尋集合類型的 `Add` 方法，其中 `Add` 方法的參數會符合集合初始化運算式中的數值型別。</span><span class="sxs-lookup"><span data-stu-id="4ee4f-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="4ee4f-104">這個 `Add` 方法是用來在集合中填入集合初始化運算式的值。</span><span class="sxs-lookup"><span data-stu-id="4ee4f-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ee4f-105">範例</span><span class="sxs-lookup"><span data-stu-id="4ee4f-105">Example</span></span>  
 <span data-ttu-id="4ee4f-106">下列範例顯示 `OrderCollection` 集合，其中包含集合初始化運算式可用來加入 `Order`類型物件的公用 `Add` 方法。</span><span class="sxs-lookup"><span data-stu-id="4ee4f-106">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="4ee4f-107">`Add` 方法可讓您使用縮短的集合初始化運算式語法。</span><span class="sxs-lookup"><span data-stu-id="4ee4f-107">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="4ee4f-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="4ee4f-108">See also</span></span>

- [<span data-ttu-id="4ee4f-109">集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="4ee4f-109">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="4ee4f-110">如何：建立集合初始設定式所使用的 Add 擴充方法</span><span class="sxs-lookup"><span data-stu-id="4ee4f-110">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)

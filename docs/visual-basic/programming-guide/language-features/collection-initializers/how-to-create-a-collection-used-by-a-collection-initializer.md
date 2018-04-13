---
title: 如何：建立集合初始設定式所使用的集合 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cff862f16530bc268628d9406ae81d23f2761926
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="7ad50-102">如何：建立集合初始設定式所使用的集合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ad50-102">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="7ad50-103">當您使用集合初始設定式來建立集合時，Visual Basic 編譯器會搜尋`Add`的集合型別的方法的參數`Add`方法符合型別集合初始設定式中的值。</span><span class="sxs-lookup"><span data-stu-id="7ad50-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="7ad50-104">這`Add`方法用來填入集合初始設定式中的值集合。</span><span class="sxs-lookup"><span data-stu-id="7ad50-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ad50-105">範例</span><span class="sxs-lookup"><span data-stu-id="7ad50-105">Example</span></span>  
 <span data-ttu-id="7ad50-106">下列範例所示`OrderCollection`集合，其中包含公用`Add`集合初始設定式可用來新增類型的物件的方法`Order`。</span><span class="sxs-lookup"><span data-stu-id="7ad50-106">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="7ad50-107">`Add`方法可讓您使用簡短的集合初始設定式語法。</span><span class="sxs-lookup"><span data-stu-id="7ad50-107">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_3.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7ad50-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ad50-108">See Also</span></span>  
 [<span data-ttu-id="7ad50-109">集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="7ad50-109">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [<span data-ttu-id="7ad50-110">如何：建立集合初始設定式所使用的 Add 擴充方法</span><span class="sxs-lookup"><span data-stu-id="7ad50-110">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)

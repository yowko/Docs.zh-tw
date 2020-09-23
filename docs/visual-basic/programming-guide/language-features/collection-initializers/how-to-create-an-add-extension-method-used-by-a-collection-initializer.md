---
title: 如何：建立集合初始設定式所使用的 Add 擴充方法
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: c36fab6635a9f7820c52c5f73c20487b92879b9a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086344"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="7ea64-102">如何：建立集合初始設定式所使用的 Add 擴充方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ea64-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>

<span data-ttu-id="7ea64-103">當您使用集合初始化運算式建立集合時，Visual Basic 編譯器會搜尋 `Add` 集合型別的方法，而該方法的參數與 `Add` 集合初始化運算式中的數值型別相符。</span><span class="sxs-lookup"><span data-stu-id="7ea64-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="7ea64-104">這個 `Add` 方法是用來在集合中填入集合初始化運算式中的值。</span><span class="sxs-lookup"><span data-stu-id="7ea64-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="7ea64-105">如果沒有相符的 `Add` 方法，且您無法修改集合的程式碼，您可以加入名為的擴充方法， `Add` 這個方法會採用集合初始化運算式所需的參數。</span><span class="sxs-lookup"><span data-stu-id="7ea64-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="7ea64-106">當您使用泛型集合的集合初始化運算式時，通常需要執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="7ea64-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ea64-107">範例</span><span class="sxs-lookup"><span data-stu-id="7ea64-107">Example</span></span>  

 <span data-ttu-id="7ea64-108">下列範例示範如何將擴充方法加入至泛型型別， <xref:System.Collections.Generic.List%601> 讓集合初始化運算式可以用來加入型別的物件 `Employee` 。</span><span class="sxs-lookup"><span data-stu-id="7ea64-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="7ea64-109">擴充方法可讓您使用縮短的集合初始化運算式語法。</span><span class="sxs-lookup"><span data-stu-id="7ea64-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="7ea64-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ea64-110">See also</span></span>

- [<span data-ttu-id="7ea64-111">集合初始化運算式</span><span class="sxs-lookup"><span data-stu-id="7ea64-111">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="7ea64-112">如何：建立集合初始設定式所使用的集合</span><span class="sxs-lookup"><span data-stu-id="7ea64-112">How to: Create a Collection Used by a Collection Initializer</span></span>](how-to-create-a-collection-used-by-a-collection-initializer.md)

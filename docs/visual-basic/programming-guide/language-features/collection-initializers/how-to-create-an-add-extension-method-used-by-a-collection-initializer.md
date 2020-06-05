---
title: 如何：建立集合初始設定式所使用的 Add 擴充方法
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 4dbe6146b70181864a6717146071f9b93a1f583e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414565"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="4da3d-102">如何：建立集合初始設定式所使用的 Add 擴充方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4da3d-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="4da3d-103">當您使用集合初始化運算式來建立集合時，Visual Basic 編譯器會搜尋 `Add` 集合類型的方法，其中方法的參數會 `Add` 符合集合初始化運算式中的數值型別。</span><span class="sxs-lookup"><span data-stu-id="4da3d-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="4da3d-104">這個 `Add` 方法是用來在集合中填入集合初始化運算式的值。</span><span class="sxs-lookup"><span data-stu-id="4da3d-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="4da3d-105">如果沒有相符 `Add` 的方法存在，而且您無法修改集合的程式碼，您可以加入名為的擴充方法，其 `Add` 會接受集合初始化運算式所需的參數。</span><span class="sxs-lookup"><span data-stu-id="4da3d-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="4da3d-106">當您使用泛型集合的集合初始化運算式時，這通常是您需要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="4da3d-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4da3d-107">範例</span><span class="sxs-lookup"><span data-stu-id="4da3d-107">Example</span></span>  
 <span data-ttu-id="4da3d-108">下列範例示範如何將擴充方法加入至泛型 <xref:System.Collections.Generic.List%601> 類型，讓集合初始化運算式可以用來加入類型的物件 `Employee` 。</span><span class="sxs-lookup"><span data-stu-id="4da3d-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="4da3d-109">擴充方法可讓您使用簡短的集合初始化運算式語法。</span><span class="sxs-lookup"><span data-stu-id="4da3d-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="4da3d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4da3d-110">See also</span></span>

- [<span data-ttu-id="4da3d-111">集合初始化運算式</span><span class="sxs-lookup"><span data-stu-id="4da3d-111">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="4da3d-112">如何：建立集合初始設定式所使用的集合</span><span class="sxs-lookup"><span data-stu-id="4da3d-112">How to: Create a Collection Used by a Collection Initializer</span></span>](how-to-create-a-collection-used-by-a-collection-initializer.md)

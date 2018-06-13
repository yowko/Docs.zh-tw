---
title: 如何：建立集合初始設定式所使用的 Add 擴充方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 5e35ad80037e843fd3cbd9caa68dcb2a09d707e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646236"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="7b729-102">如何：建立集合初始設定式所使用的 Add 擴充方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b729-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="7b729-103">當您使用集合初始設定式來建立集合時，Visual Basic 編譯器會搜尋`Add`的集合型別的方法的參數`Add`方法符合型別集合初始設定式中的值。</span><span class="sxs-lookup"><span data-stu-id="7b729-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="7b729-104">這`Add`方法用來填入集合初始設定式中的值集合。</span><span class="sxs-lookup"><span data-stu-id="7b729-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="7b729-105">如果沒有相符的`Add`方法的存在，您無法修改集合的程式碼，您可以加入擴充方法呼叫`Add`採用所需的集合初始設定式的參數。</span><span class="sxs-lookup"><span data-stu-id="7b729-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="7b729-106">這通常是您需要時，您可以使用集合初始設定式的泛型集合。</span><span class="sxs-lookup"><span data-stu-id="7b729-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b729-107">範例</span><span class="sxs-lookup"><span data-stu-id="7b729-107">Example</span></span>  
 <span data-ttu-id="7b729-108">下列範例示範如何將擴充方法新增至泛型<xref:System.Collections.Generic.List%601>型別，如此集合初始設定式可以用來加入類型的物件`Employee`。</span><span class="sxs-lookup"><span data-stu-id="7b729-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="7b729-109">擴充方法可讓您使用簡短的集合初始設定式語法。</span><span class="sxs-lookup"><span data-stu-id="7b729-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7b729-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b729-110">See Also</span></span>  
 [<span data-ttu-id="7b729-111">集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="7b729-111">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [<span data-ttu-id="7b729-112">如何：建立集合初始設定式所使用的集合</span><span class="sxs-lookup"><span data-stu-id="7b729-112">How to: Create a Collection Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)

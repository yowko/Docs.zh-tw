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
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="30a2d-102">HOW TO：建立 Add 擴充方法使用集合初始設定式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30a2d-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="30a2d-103">當您使用集合初始設定式來建立集合時，Visual Basic 編譯器會搜尋`Add`的集合型別的方法的參數`Add`方法符合集合初始設定式中的值型別。</span><span class="sxs-lookup"><span data-stu-id="30a2d-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="30a2d-104">這`Add`方法用來擴展集合，集合初始設定式中的值。</span><span class="sxs-lookup"><span data-stu-id="30a2d-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="30a2d-105">如果沒有相符`Add`方法存在，您無法修改集合的程式碼，您可以加入擴充方法呼叫`Add`採用所需的集合初始設定式的參數。</span><span class="sxs-lookup"><span data-stu-id="30a2d-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="30a2d-106">這通常是您需要您針對泛型集合使用集合初始設定式時執行的作業。</span><span class="sxs-lookup"><span data-stu-id="30a2d-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30a2d-107">範例</span><span class="sxs-lookup"><span data-stu-id="30a2d-107">Example</span></span>  
 <span data-ttu-id="30a2d-108">下列範例示範如何將擴充方法新增至泛型<xref:System.Collections.Generic.List%601>類型，讓集合初始設定式可以用來加入型別之物件`Employee`。</span><span class="sxs-lookup"><span data-stu-id="30a2d-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="30a2d-109">擴充方法可讓您使用簡短的集合初始設定式語法。</span><span class="sxs-lookup"><span data-stu-id="30a2d-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="30a2d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30a2d-110">See also</span></span>

- [<span data-ttu-id="30a2d-111">集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="30a2d-111">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="30a2d-112">如何：建立集合，集合初始設定式使用</span><span class="sxs-lookup"><span data-stu-id="30a2d-112">How to: Create a Collection Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)

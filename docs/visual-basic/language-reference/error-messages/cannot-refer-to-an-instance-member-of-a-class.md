---
title: 沒有類別的明確執行個體，因此無法從共用方法或共用成員初始設定式中參考至類別的執行個體成員
ms.date: 07/20/2015
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
ms.openlocfilehash: aad068b5857eb956ded63fa2a57cb163d3cf5c58
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322689"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a><span data-ttu-id="c1324-102">沒有類別的明確執行個體，因此無法從共用方法或共用成員初始設定式中參考至類別的執行個體成員</span><span class="sxs-lookup"><span data-stu-id="c1324-102">Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class</span></span>
<span data-ttu-id="c1324-103">您嘗試參考非共用的成員共用的程序內的類別。</span><span class="sxs-lookup"><span data-stu-id="c1324-103">You have tried to refer to a non-shared member of a class from within a shared procedure.</span></span> <span data-ttu-id="c1324-104">下列範例會示範這種情況。</span><span class="sxs-lookup"><span data-stu-id="c1324-104">The following example demonstrates such a situation.</span></span>  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="c1324-105">在上述範例中，指派陳述式`x = 10`會產生此錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c1324-105">In the preceding example, the assignment statement `x = 10` generates this error message.</span></span> <span data-ttu-id="c1324-106">這是因為共用的程序嘗試存取執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="c1324-106">This is because a shared procedure is attempting to access an instance variable.</span></span>  
  
 <span data-ttu-id="c1324-107">變數`x`是執行個體成員，因為它未宣告為[共用](../../../visual-basic/language-reference/modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="c1324-107">The variable `x` is an instance member because it is not declared as [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="c1324-108">每個類別執行個體`sample`包含它自己的個別變數`x`。</span><span class="sxs-lookup"><span data-stu-id="c1324-108">Each instance of class `sample` contains its own individual variable `x`.</span></span> <span data-ttu-id="c1324-109">當某個執行個體設定或變更的值`x`，它不會影響值`x`中任何其他執行個體。</span><span class="sxs-lookup"><span data-stu-id="c1324-109">When one instance sets or changes the value of `x`, it does not affect the value of `x` in any other instance.</span></span>  
  
 <span data-ttu-id="c1324-110">不過，此程序`setX`已`Shared`類別的所有執行個體之間`sample`。</span><span class="sxs-lookup"><span data-stu-id="c1324-110">However, the procedure `setX` is `Shared` among all instances of class `sample`.</span></span> <span data-ttu-id="c1324-111">這表示它不是類別的任何一個執行個體相關聯，但而不是個別的執行個體獨立運作。</span><span class="sxs-lookup"><span data-stu-id="c1324-111">This means it is not associated with any one instance of the class, but rather operates independently of individual instances.</span></span> <span data-ttu-id="c1324-112">因為它有沒有特定的執行個體，連接`setX`無法存取執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="c1324-112">Because it has no connection with a particular instance, `setX` cannot access an instance variable.</span></span> <span data-ttu-id="c1324-113">它必須只在運作`Shared`變數。</span><span class="sxs-lookup"><span data-stu-id="c1324-113">It must operate only on `Shared` variables.</span></span> <span data-ttu-id="c1324-114">當`setX`設定或變更共用的變數，新的值可供類別的所有執行個體的值。</span><span class="sxs-lookup"><span data-stu-id="c1324-114">When `setX` sets or changes the value of a shared variable, that new value is available to all instances of the class.</span></span>  
  
 <span data-ttu-id="c1324-115">**錯誤 ID:** BC30369</span><span class="sxs-lookup"><span data-stu-id="c1324-115">**Error ID:** BC30369</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c1324-116">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c1324-116">To correct this error</span></span>  
  
1. <span data-ttu-id="c1324-117">決定是否要在類別中的所有執行個體之間共用或保留每個執行個體的個別成員。</span><span class="sxs-lookup"><span data-stu-id="c1324-117">Decide whether you want the member to be shared among all instances of the class, or kept individual for each instance.</span></span>  
  
2. <span data-ttu-id="c1324-118">如果您想要在所有執行個體之間共用之成員的單一複本，新增`Shared`成員宣告的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c1324-118">If you want a single copy of the member to be shared among all instances, add the `Shared` keyword to the member declaration.</span></span> <span data-ttu-id="c1324-119">保留`Shared`程序宣告中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c1324-119">Retain the `Shared` keyword in the procedure declaration.</span></span>  
  
3. <span data-ttu-id="c1324-120">如果您想要有自己的個別複本成員的每個執行個體時，請勿指定`Shared`成員宣告。</span><span class="sxs-lookup"><span data-stu-id="c1324-120">If you want each instance to have its own individual copy of the member, do not specify `Shared` for the member declaration.</span></span> <span data-ttu-id="c1324-121">移除`Shared`從程序宣告的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c1324-121">Remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1324-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1324-122">See also</span></span>

- [<span data-ttu-id="c1324-123">Shared</span><span class="sxs-lookup"><span data-stu-id="c1324-123">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)

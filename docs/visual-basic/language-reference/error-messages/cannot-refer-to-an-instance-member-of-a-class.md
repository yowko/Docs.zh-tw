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
ms.openlocfilehash: 9b388685299469d5865d57b698e3a66de912fa84
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250198"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a><span data-ttu-id="7a287-102">沒有類別的明確執行個體，因此無法從共用方法或共用成員初始設定式中參考至類別的執行個體成員</span><span class="sxs-lookup"><span data-stu-id="7a287-102">Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class</span></span>

<span data-ttu-id="7a287-103">您已嘗試從共用的程式中參考類別的非共用成員。</span><span class="sxs-lookup"><span data-stu-id="7a287-103">You have tried to refer to a non-shared member of a class from within a shared procedure.</span></span> <span data-ttu-id="7a287-104">下列範例示範這種情況：</span><span class="sxs-lookup"><span data-stu-id="7a287-104">The following example demonstrates such a situation:</span></span>
  
```vb  
Class Sample
    Public x as Integer  
    Public Shared Sub SetX()
        x = 10  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="7a287-105">在上述範例中，指派語句 `x = 10` 會產生這個錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="7a287-105">In the preceding example, the assignment statement `x = 10` generates this error message.</span></span> <span data-ttu-id="7a287-106">這是因為共用程式嘗試存取執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="7a287-106">This is because a shared procedure is attempting to access an instance variable.</span></span>  
  
 <span data-ttu-id="7a287-107">變數 `x` 是實例成員，因為它並未宣告為[Shared](../modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="7a287-107">The variable `x` is an instance member because it is not declared as [Shared](../modifiers/shared.md).</span></span> <span data-ttu-id="7a287-108">類別的每個實例 `Sample` 都包含自己的個別變數 `x`。</span><span class="sxs-lookup"><span data-stu-id="7a287-108">Each instance of class `Sample` contains its own individual variable `x`.</span></span> <span data-ttu-id="7a287-109">當某個實例設定或變更 `x` 的值時，不會影響任何其他實例中 `x` 的值。</span><span class="sxs-lookup"><span data-stu-id="7a287-109">When one instance sets or changes the value of `x`, it does not affect the value of `x` in any other instance.</span></span>
  
 <span data-ttu-id="7a287-110">不過，在類別 `Sample` 的所有實例中，`SetX` 的程式 `Shared`。</span><span class="sxs-lookup"><span data-stu-id="7a287-110">However, the procedure `SetX` is `Shared` among all instances of class `Sample`.</span></span> <span data-ttu-id="7a287-111">這表示它不會與類別的任何一個實例相關聯，而是獨立于個別實例運作。</span><span class="sxs-lookup"><span data-stu-id="7a287-111">This means it is not associated with any one instance of the class, but rather operates independently of individual instances.</span></span> <span data-ttu-id="7a287-112">因為它沒有與特定實例的連接，所以 `setX` 無法存取執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="7a287-112">Because it has no connection with a particular instance, `setX` cannot access an instance variable.</span></span> <span data-ttu-id="7a287-113">它必須只在 `Shared` 變數上運作。</span><span class="sxs-lookup"><span data-stu-id="7a287-113">It must operate only on `Shared` variables.</span></span> <span data-ttu-id="7a287-114">當 `SetX` 設定或變更共用變數的值時，該新值可供類別的所有實例使用。</span><span class="sxs-lookup"><span data-stu-id="7a287-114">When `SetX` sets or changes the value of a shared variable, that new value is available to all instances of the class.</span></span>
  
 <span data-ttu-id="7a287-115">**錯誤識別碼：** BC30369</span><span class="sxs-lookup"><span data-stu-id="7a287-115">**Error ID:** BC30369</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7a287-116">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="7a287-116">To correct this error</span></span>
  
1. <span data-ttu-id="7a287-117">決定您是否要在類別的所有實例之間共用成員，或為每個實例保留個人。</span><span class="sxs-lookup"><span data-stu-id="7a287-117">Decide whether you want the member to be shared among all instances of the class, or kept individual for each instance.</span></span>

2. <span data-ttu-id="7a287-118">如果您想要在所有實例之間共用成員的單一複本，請將 `Shared` 關鍵字加入至成員宣告。</span><span class="sxs-lookup"><span data-stu-id="7a287-118">If you want a single copy of the member to be shared among all instances, add the `Shared` keyword to the member declaration.</span></span> <span data-ttu-id="7a287-119">在程式宣告中保留 `Shared` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7a287-119">Retain the `Shared` keyword in the procedure declaration.</span></span>

3. <span data-ttu-id="7a287-120">如果您想要讓每個實例擁有其本身的個別複本，請勿針對成員宣告指定 `Shared`。</span><span class="sxs-lookup"><span data-stu-id="7a287-120">If you want each instance to have its own individual copy of the member, do not specify `Shared` for the member declaration.</span></span> <span data-ttu-id="7a287-121">請從程式宣告中移除 `Shared` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7a287-121">Remove the `Shared` keyword from the procedure declaration.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7a287-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a287-122">See also</span></span>

- [<span data-ttu-id="7a287-123">Shared</span><span class="sxs-lookup"><span data-stu-id="7a287-123">Shared</span></span>](../modifiers/shared.md)

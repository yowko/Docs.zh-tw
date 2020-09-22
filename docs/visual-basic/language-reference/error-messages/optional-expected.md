---
title: 必須是 'Optional'
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: e212939cf814a9ac632571b2203f2f256dea61ae
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873602"
---
# <a name="optional-expected"></a><span data-ttu-id="4d379-102">必須是 'Optional'</span><span class="sxs-lookup"><span data-stu-id="4d379-102">'Optional' expected</span></span>

<span data-ttu-id="4d379-103">程式聲明中的選擇性引數後面接著必要的引數。</span><span class="sxs-lookup"><span data-stu-id="4d379-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="4d379-104">選擇性引數後面的每個引數也必須是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="4d379-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="4d379-105">**錯誤識別碼：** BC30202</span><span class="sxs-lookup"><span data-stu-id="4d379-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4d379-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4d379-106">To correct this error</span></span>  
  
1. <span data-ttu-id="4d379-107">如果需要引數，請將其移至引數清單中的第一個選擇性引數前面。</span><span class="sxs-lookup"><span data-stu-id="4d379-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2. <span data-ttu-id="4d379-108">如果引數是選擇性的，請使用 `Optional` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4d379-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d379-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d379-109">See also</span></span>

- [<span data-ttu-id="4d379-110">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="4d379-110">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)

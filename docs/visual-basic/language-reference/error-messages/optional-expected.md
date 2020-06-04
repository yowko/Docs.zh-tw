---
title: 必須是 'Optional'
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 411e3248409ab0184666f4efefb4ec4becf7cab1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409344"
---
# <a name="optional-expected"></a><span data-ttu-id="f80e6-102">必須是 'Optional'</span><span class="sxs-lookup"><span data-stu-id="f80e6-102">'Optional' expected</span></span>
<span data-ttu-id="f80e6-103">程式宣告中的選擇性引數後面接著必要的引數。</span><span class="sxs-lookup"><span data-stu-id="f80e6-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="f80e6-104">選擇性引數之後的每個引數也必須是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="f80e6-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="f80e6-105">**錯誤識別碼：** BC30202</span><span class="sxs-lookup"><span data-stu-id="f80e6-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f80e6-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f80e6-106">To correct this error</span></span>  
  
1. <span data-ttu-id="f80e6-107">如果需要引數，請將它移至引數清單中的第一個選擇性引數之前。</span><span class="sxs-lookup"><span data-stu-id="f80e6-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2. <span data-ttu-id="f80e6-108">如果引數是選擇性的，請使用 `Optional` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f80e6-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f80e6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f80e6-109">See also</span></span>

- [<span data-ttu-id="f80e6-110">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="f80e6-110">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)

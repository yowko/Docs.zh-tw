---
title: '&#39;選擇性&#39;預期'
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 52e4288255a246f78730b33beb55f6d2d83ff214
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593950"
---
# <a name="39optional39-expected"></a><span data-ttu-id="40a91-102">&#39;選擇性&#39;預期</span><span class="sxs-lookup"><span data-stu-id="40a91-102">&#39;Optional&#39; expected</span></span>
<span data-ttu-id="40a91-103">在程序宣告中的選擇性引數的後面是必要的引數。</span><span class="sxs-lookup"><span data-stu-id="40a91-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="40a91-104">每個選擇性引數後面的引數也必須是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="40a91-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="40a91-105">**錯誤 ID:** BC30202</span><span class="sxs-lookup"><span data-stu-id="40a91-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="40a91-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="40a91-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="40a91-107">如果引數要為必要，將它移至引數清單中前面的第一個選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="40a91-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="40a91-108">如果引數是選擇性的使用`Optional`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="40a91-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40a91-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40a91-109">See Also</span></span>  
 [<span data-ttu-id="40a91-110">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="40a91-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)

---
title: 必須是 'Optional'
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 71a25784f357a7e596093b314ed5b3d721d6f92c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946584"
---
# <a name="optional-expected"></a><span data-ttu-id="798f7-102">必須是 'Optional'</span><span class="sxs-lookup"><span data-stu-id="798f7-102">'Optional' expected</span></span>
<span data-ttu-id="798f7-103">在程序宣告中的選擇性引數的後面是必要的引數。</span><span class="sxs-lookup"><span data-stu-id="798f7-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="798f7-104">下列選擇性引數的每個引數也必須是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="798f7-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="798f7-105">**錯誤 ID:** BC30202</span><span class="sxs-lookup"><span data-stu-id="798f7-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="798f7-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="798f7-106">To correct this error</span></span>  
  
1. <span data-ttu-id="798f7-107">如果引數是必要，將它移至引數清單中前面的第一個選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="798f7-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2. <span data-ttu-id="798f7-108">引數是選擇性，如果使用`Optional`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="798f7-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="798f7-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="798f7-109">See also</span></span>

- [<span data-ttu-id="798f7-110">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="798f7-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)

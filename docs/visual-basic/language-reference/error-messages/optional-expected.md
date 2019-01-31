---
title: 必須是 'Optional'
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 0ad0d0890b73103a0678b13409a24190329d37d4
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266319"
---
# <a name="optional-expected"></a><span data-ttu-id="0e50a-102">必須是 'Optional'</span><span class="sxs-lookup"><span data-stu-id="0e50a-102">'Optional' expected</span></span>
<span data-ttu-id="0e50a-103">在程序宣告中的選擇性引數的後面是必要的引數。</span><span class="sxs-lookup"><span data-stu-id="0e50a-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="0e50a-104">下列選擇性引數的每個引數也必須是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="0e50a-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="0e50a-105">**錯誤 ID:** BC30202</span><span class="sxs-lookup"><span data-stu-id="0e50a-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0e50a-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="0e50a-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="0e50a-107">如果引數是必要，將它移至引數清單中前面的第一個選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="0e50a-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="0e50a-108">引數是選擇性，如果使用`Optional`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0e50a-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e50a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e50a-109">See also</span></span>
- [<span data-ttu-id="0e50a-110">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="0e50a-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)

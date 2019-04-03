---
title: 必須是 'Optional'
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: d70a71f8b5f72edbd7f3e50bc099360d02e95389
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840545"
---
# <a name="optional-expected"></a><span data-ttu-id="d7e42-102">必須是 'Optional'</span><span class="sxs-lookup"><span data-stu-id="d7e42-102">'Optional' expected</span></span>
<span data-ttu-id="d7e42-103">在程序宣告中的選擇性引數的後面是必要的引數。</span><span class="sxs-lookup"><span data-stu-id="d7e42-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="d7e42-104">下列選擇性引數的每個引數也必須是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="d7e42-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="d7e42-105">**錯誤 ID:** BC30202</span><span class="sxs-lookup"><span data-stu-id="d7e42-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d7e42-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d7e42-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="d7e42-107">如果引數是必要，將它移至引數清單中前面的第一個選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="d7e42-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="d7e42-108">引數是選擇性，如果使用`Optional`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d7e42-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7e42-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7e42-109">See also</span></span>

- [<span data-ttu-id="d7e42-110">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="d7e42-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)

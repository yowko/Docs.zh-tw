---
title: 引數不是選擇性的 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID449
ms.assetid: 76e7bcf3-24ed-4cd5-945b-b98f1c76944b
ms.openlocfilehash: 2004cf10d7827ac7b77773459de8158449136239
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683134"
---
# <a name="argument-not-optional-visual-basic"></a><span data-ttu-id="344c8-102">引數不是選擇性的 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="344c8-102">Argument not optional (Visual Basic)</span></span>
<span data-ttu-id="344c8-103">引數類型與數量必須符合所預期。</span><span class="sxs-lookup"><span data-stu-id="344c8-103">The number and types of arguments must match those expected.</span></span> <span data-ttu-id="344c8-104">可能是沒有引數數目不正確，或省略的引數不是選擇性。</span><span class="sxs-lookup"><span data-stu-id="344c8-104">Either there is an incorrect number of arguments, or an omitted argument is not optional.</span></span> <span data-ttu-id="344c8-105">引數可以只從使用者定義的程序呼叫省略，如果它已宣告`Optional`程序定義中。</span><span class="sxs-lookup"><span data-stu-id="344c8-105">An argument can only be omitted from a call to a user-defined procedure if it was declared `Optional` in the procedure definition.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="344c8-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="344c8-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="344c8-107">提供所有必要的引數。</span><span class="sxs-lookup"><span data-stu-id="344c8-107">Supply all necessary arguments.</span></span>  
  
2.  <span data-ttu-id="344c8-108">請確定省略的引數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="344c8-108">Make sure omitted arguments are optional.</span></span> <span data-ttu-id="344c8-109">如果他們不這樣做，請提供在呼叫中，引數，或是將參數宣告`Optional`定義中。</span><span class="sxs-lookup"><span data-stu-id="344c8-109">If they are not, either supply the argument in the call, or declare the parameter `Optional` in the definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="344c8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="344c8-110">See also</span></span>
- [<span data-ttu-id="344c8-111">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="344c8-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)

---
title: 引數不是選擇性
ms.date: 07/20/2015
f1_keywords:
- vbrID449
ms.assetid: 76e7bcf3-24ed-4cd5-945b-b98f1c76944b
ms.openlocfilehash: 043d126b07838f1a98788021048e5f22e3bc42ed
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353905"
---
# <a name="argument-not-optional-visual-basic"></a><span data-ttu-id="406b1-102">引數不是選擇性的 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="406b1-102">Argument not optional (Visual Basic)</span></span>

<span data-ttu-id="406b1-103">引數的數目和類型必須符合預期。</span><span class="sxs-lookup"><span data-stu-id="406b1-103">The number and types of arguments must match those expected.</span></span> <span data-ttu-id="406b1-104">可能是引數數目不正確，或省略的引數不是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="406b1-104">Either there is an incorrect number of arguments, or an omitted argument is not optional.</span></span> <span data-ttu-id="406b1-105">如果引數是在程序定義中 `Optional` 宣告，則只能從呼叫使用者定義的程式中省略。</span><span class="sxs-lookup"><span data-stu-id="406b1-105">An argument can only be omitted from a call to a user-defined procedure if it was declared `Optional` in the procedure definition.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="406b1-106">若要改正這項錯誤</span><span class="sxs-lookup"><span data-stu-id="406b1-106">To correct this error</span></span>  
  
1. <span data-ttu-id="406b1-107">提供所有必要的引數。</span><span class="sxs-lookup"><span data-stu-id="406b1-107">Supply all necessary arguments.</span></span>  
  
2. <span data-ttu-id="406b1-108">請確定省略的引數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="406b1-108">Make sure omitted arguments are optional.</span></span> <span data-ttu-id="406b1-109">如果不是，請在呼叫中提供引數，或在定義中宣告參數 `Optional`。</span><span class="sxs-lookup"><span data-stu-id="406b1-109">If they are not, either supply the argument in the call, or declare the parameter `Optional` in the definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="406b1-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="406b1-110">See also</span></span>

- [<span data-ttu-id="406b1-111">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="406b1-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)

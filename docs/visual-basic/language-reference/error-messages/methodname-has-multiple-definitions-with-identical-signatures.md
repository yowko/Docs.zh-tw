---
title: "'<methodname>' 有多個具相同簽名碼的定義"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 2934a5666c55e1ca57b91ab86585261e6d71a2d3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873734"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="60c16-102">'\<methodname>' 有多個具相同簽名碼的定義</span><span class="sxs-lookup"><span data-stu-id="60c16-102">'\<methodname>' has multiple definitions with identical signatures</span></span>

<span data-ttu-id="60c16-103">`Function`或程式 `Sub` 聲明使用相同的程式名稱和引數清單做為先前的宣告。</span><span class="sxs-lookup"><span data-stu-id="60c16-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="60c16-104">其中一個可能的原因是嘗試多載原始程式。</span><span class="sxs-lookup"><span data-stu-id="60c16-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="60c16-105">多載程式必須有不同的引數清單。</span><span class="sxs-lookup"><span data-stu-id="60c16-105">Overloaded procedures must have different argument lists.</span></span>  
  
 <span data-ttu-id="60c16-106">**錯誤識別碼：** BC30269</span><span class="sxs-lookup"><span data-stu-id="60c16-106">**Error ID:** BC30269</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="60c16-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="60c16-107">To correct this error</span></span>  
  
- <span data-ttu-id="60c16-108">請變更程式名稱或引數清單，或移除重複的宣告。</span><span class="sxs-lookup"><span data-stu-id="60c16-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c16-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60c16-109">See also</span></span>

- [<span data-ttu-id="60c16-110">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="60c16-110">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="60c16-111">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="60c16-111">Considerations in Overloading Procedures</span></span>](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)

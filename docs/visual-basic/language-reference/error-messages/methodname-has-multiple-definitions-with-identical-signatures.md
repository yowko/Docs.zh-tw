---
title: "'<methodname>' 有多個具相同簽名碼的定義"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: fe8d1d8e11e25bcd79894ed82a57dd06748c3d68
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831874"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="29a7e-102">'\<方法名稱 >' 有多個具相同簽章的定義</span><span class="sxs-lookup"><span data-stu-id="29a7e-102">'\<methodname>' has multiple definitions with identical signatures</span></span>
<span data-ttu-id="29a7e-103">A`Function`或`Sub`程序宣告為上一個宣告中使用相同的程序名稱和引數清單。</span><span class="sxs-lookup"><span data-stu-id="29a7e-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="29a7e-104">其中一個可能的原因是嘗試多載，原始的程序。</span><span class="sxs-lookup"><span data-stu-id="29a7e-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="29a7e-105">多載程序必須有不同的引數清單。</span><span class="sxs-lookup"><span data-stu-id="29a7e-105">Overloaded procedures must have different argument lists.</span></span>  
  
 <span data-ttu-id="29a7e-106">**錯誤 ID:** BC30269</span><span class="sxs-lookup"><span data-stu-id="29a7e-106">**Error ID:** BC30269</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="29a7e-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="29a7e-107">To correct this error</span></span>  
  
-   <span data-ttu-id="29a7e-108">變更的程序名稱或引數清單中，或移除重複的宣告。</span><span class="sxs-lookup"><span data-stu-id="29a7e-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29a7e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29a7e-109">See also</span></span>

- [<span data-ttu-id="29a7e-110">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="29a7e-110">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="29a7e-111">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="29a7e-111">Considerations in Overloading Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)

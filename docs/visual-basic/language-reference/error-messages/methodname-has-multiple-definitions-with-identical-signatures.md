---
title: "'<methodname>' 有多個具相同簽名碼的定義"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 97113227591c40f302d3d1a08a4248a8199817bc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285424"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="70d9a-102">'\<方法名稱 >' 有多個具相同簽章的定義</span><span class="sxs-lookup"><span data-stu-id="70d9a-102">'\<methodname>' has multiple definitions with identical signatures</span></span>
<span data-ttu-id="70d9a-103">A`Function`或`Sub`程序宣告為上一個宣告中使用相同的程序名稱和引數清單。</span><span class="sxs-lookup"><span data-stu-id="70d9a-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="70d9a-104">其中一個可能的原因是嘗試多載，原始的程序。</span><span class="sxs-lookup"><span data-stu-id="70d9a-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="70d9a-105">多載程序必須有不同的引數清單。</span><span class="sxs-lookup"><span data-stu-id="70d9a-105">Overloaded procedures must have different argument lists.</span></span>  
  
 <span data-ttu-id="70d9a-106">**錯誤 ID:** BC30269</span><span class="sxs-lookup"><span data-stu-id="70d9a-106">**Error ID:** BC30269</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="70d9a-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="70d9a-107">To correct this error</span></span>  
  
-   <span data-ttu-id="70d9a-108">變更的程序名稱或引數清單中，或移除重複的宣告。</span><span class="sxs-lookup"><span data-stu-id="70d9a-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70d9a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70d9a-109">See also</span></span>
- [<span data-ttu-id="70d9a-110">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="70d9a-110">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="70d9a-111">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="70d9a-111">Considerations in Overloading Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)

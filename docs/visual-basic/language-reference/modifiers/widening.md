---
title: Widening
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: 69040bf48b44a54f7a231738b88db1cbc716ebb3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359899"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="cd834-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd834-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="cd834-103">表示轉換運算子（ `CType` ）會將類別或結構轉換成可保存原始類別或結構之所有可能值的類型。</span><span class="sxs-lookup"><span data-stu-id="cd834-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="cd834-104">使用加寬關鍵字進行轉換</span><span class="sxs-lookup"><span data-stu-id="cd834-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="cd834-105">轉換程式 `Public Shared` 除了之外，還必須指定 `Widening` 。</span><span class="sxs-lookup"><span data-stu-id="cd834-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="cd834-106">擴輾轉換一律會在執行時間成功，而且永遠不會產生資料遺失。</span><span class="sxs-lookup"><span data-stu-id="cd834-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="cd834-107">範例包括 `Single` 對 `Double` `Char` `String` 其基底類型的、至和衍生類型。</span><span class="sxs-lookup"><span data-stu-id="cd834-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="cd834-108">最後一次轉換是擴大的，因為衍生類型包含基底類型的所有成員，因此是基底類型的實例。</span><span class="sxs-lookup"><span data-stu-id="cd834-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="cd834-109">使用程式碼不需要用於 `CType` 擴輾轉換，即使 `Option Strict` 為 `On` 。</span><span class="sxs-lookup"><span data-stu-id="cd834-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="cd834-110">`Widening`關鍵字可以在此內容中使用：</span><span class="sxs-lookup"><span data-stu-id="cd834-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="cd834-111">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="cd834-111">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 <span data-ttu-id="cd834-112">如需擴展和縮小轉換運算子的範例定義，請參閱[如何：定義轉換運算子](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="cd834-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd834-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd834-113">See also</span></span>

- [<span data-ttu-id="cd834-114">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="cd834-114">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="cd834-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="cd834-115">Narrowing</span></span>](narrowing.md)
- [<span data-ttu-id="cd834-116">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="cd834-116">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="cd834-117">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="cd834-117">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="cd834-118">CType Function</span><span class="sxs-lookup"><span data-stu-id="cd834-118">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="cd834-119">Long</span><span class="sxs-lookup"><span data-stu-id="cd834-119">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="cd834-120">How to: Define a Conversion Operator</span><span class="sxs-lookup"><span data-stu-id="cd834-120">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)

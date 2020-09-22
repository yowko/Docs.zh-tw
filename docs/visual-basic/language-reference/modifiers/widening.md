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
ms.openlocfilehash: 14e0b026f4fc3b0bf202ea643a28d6f1a7df2b7c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867644"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="8018a-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8018a-102">Widening (Visual Basic)</span></span>

<span data-ttu-id="8018a-103">指出轉換運算子 (`CType`) 將類別或結構轉換成可保存原始類別或結構之所有可能值的型別。</span><span class="sxs-lookup"><span data-stu-id="8018a-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="8018a-104">使用擴展關鍵字進行轉換</span><span class="sxs-lookup"><span data-stu-id="8018a-104">Converting with the Widening Keyword</span></span>  

 <span data-ttu-id="8018a-105">除了以外，轉換程式 `Public Shared` 還必須指定 `Widening` 。</span><span class="sxs-lookup"><span data-stu-id="8018a-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="8018a-106">擴輾轉換一律會在執行時間成功，且不會產生資料遺失。</span><span class="sxs-lookup"><span data-stu-id="8018a-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="8018a-107">範例為 `Single` `Double` `Char` `String` 其基底類型的、到和衍生型別。</span><span class="sxs-lookup"><span data-stu-id="8018a-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="8018a-108">這項最後的轉換是擴展的，因為衍生型別包含基底類型的所有成員，因此是基底類型的實例。</span><span class="sxs-lookup"><span data-stu-id="8018a-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="8018a-109">使用程式碼不一定要用於 `CType` 擴輾轉換，即使 `Option Strict` 是 `On` 。</span><span class="sxs-lookup"><span data-stu-id="8018a-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="8018a-110">`Widening`關鍵字可用於此內容中：</span><span class="sxs-lookup"><span data-stu-id="8018a-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="8018a-111">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="8018a-111">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 <span data-ttu-id="8018a-112">如需擴展和縮小轉換運算子的範例定義，請參閱 [如何：定義轉換運算子](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="8018a-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8018a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8018a-113">See also</span></span>

- [<span data-ttu-id="8018a-114">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="8018a-114">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="8018a-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="8018a-115">Narrowing</span></span>](narrowing.md)
- [<span data-ttu-id="8018a-116">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="8018a-116">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="8018a-117">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="8018a-117">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="8018a-118">CType Function</span><span class="sxs-lookup"><span data-stu-id="8018a-118">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="8018a-119">Long</span><span class="sxs-lookup"><span data-stu-id="8018a-119">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="8018a-120">How to: Define a Conversion Operator</span><span class="sxs-lookup"><span data-stu-id="8018a-120">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)

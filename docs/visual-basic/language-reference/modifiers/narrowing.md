---
title: Narrowing
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: f7724053e3732c909523e4e2d3b65bb1918c29d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362355"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="9c53a-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c53a-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="9c53a-103">表示轉換運算子（ `CType` ）會將類別或結構轉換成可能無法保存原始類別或結構之某些可能值的類型。</span><span class="sxs-lookup"><span data-stu-id="9c53a-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="9c53a-104">使用縮小關鍵字進行轉換</span><span class="sxs-lookup"><span data-stu-id="9c53a-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="9c53a-105">轉換程式 `Public Shared` 除了之外，還必須指定 `Narrowing` 。</span><span class="sxs-lookup"><span data-stu-id="9c53a-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="9c53a-106">縮小轉換在執行時間不一定會成功，而且可能會失敗或產生資料遺失。</span><span class="sxs-lookup"><span data-stu-id="9c53a-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="9c53a-107">範例包括 `Long` 對 `Integer` `String` 衍生類型的、至以及 `Date` 基底類型。</span><span class="sxs-lookup"><span data-stu-id="9c53a-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="9c53a-108">最後一個轉換會縮小，因為基底類型可能不包含衍生類型的所有成員，因此不是衍生類型的實例。</span><span class="sxs-lookup"><span data-stu-id="9c53a-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="9c53a-109">如果 `Option Strict` 為 `On` ，則取用程式碼必須用於 `CType` 所有縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="9c53a-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="9c53a-110">`Narrowing`關鍵字可以在此內容中使用：</span><span class="sxs-lookup"><span data-stu-id="9c53a-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="9c53a-111">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="9c53a-111">Operator Statement</span></span>](../statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9c53a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c53a-112">See also</span></span>

- [<span data-ttu-id="9c53a-113">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="9c53a-113">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="9c53a-114">Widening</span><span class="sxs-lookup"><span data-stu-id="9c53a-114">Widening</span></span>](widening.md)
- [<span data-ttu-id="9c53a-115">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="9c53a-115">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="9c53a-116">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="9c53a-116">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="9c53a-117">CType Function</span><span class="sxs-lookup"><span data-stu-id="9c53a-117">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="9c53a-118">Long</span><span class="sxs-lookup"><span data-stu-id="9c53a-118">Option Strict Statement</span></span>](../statements/option-strict-statement.md)

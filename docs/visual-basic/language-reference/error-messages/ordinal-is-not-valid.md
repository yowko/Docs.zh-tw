---
title: 無效的序數
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: f3207c2cc237ae22c295c2b3ed56f18601625226
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822243"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="9a78c-102">無效的序數</span><span class="sxs-lookup"><span data-stu-id="9a78c-102">Ordinal is not valid</span></span>
<span data-ttu-id="9a78c-103">您的動態連結程式庫 (DLL) 的呼叫表示使用的數字，而不是程序名稱，使用`#num`語法。</span><span class="sxs-lookup"><span data-stu-id="9a78c-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="9a78c-104">此錯誤有下列可能的原因：</span><span class="sxs-lookup"><span data-stu-id="9a78c-104">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="9a78c-105">嘗試將轉換`#num`失敗為序數的運算式。</span><span class="sxs-lookup"><span data-stu-id="9a78c-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
-   <span data-ttu-id="9a78c-106">`#num`指定 DLL 中未指定任何函式。</span><span class="sxs-lookup"><span data-stu-id="9a78c-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
-   <span data-ttu-id="9a78c-107">類型程式庫有無效的宣告，因而導致無效的序數數字的內部使用。</span><span class="sxs-lookup"><span data-stu-id="9a78c-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9a78c-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="9a78c-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="9a78c-109">請確認運算式代表有效的數字，或呼叫程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="9a78c-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2.  <span data-ttu-id="9a78c-110">請確定`#num`識別有效的函式在 DLL 中。</span><span class="sxs-lookup"><span data-stu-id="9a78c-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3.  <span data-ttu-id="9a78c-111">找出造成問題註解的程式碼的程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="9a78c-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="9a78c-112">撰寫`Declare`陳述式的程序和報表類型程式庫的供應商的問題。</span><span class="sxs-lookup"><span data-stu-id="9a78c-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a78c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a78c-113">See also</span></span>

- [<span data-ttu-id="9a78c-114">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="9a78c-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

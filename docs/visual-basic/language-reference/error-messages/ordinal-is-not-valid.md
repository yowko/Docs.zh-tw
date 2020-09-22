---
title: 無效的序數
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 64f56b2ecace0ceafb310a175ea605e6959b7256
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871393"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="c3425-102">無效的序數</span><span class="sxs-lookup"><span data-stu-id="c3425-102">Ordinal is not valid</span></span>

<span data-ttu-id="c3425-103">您對動態連結程式庫的呼叫 (DLL) 指出要使用數位，而不是程式名稱（使用語法） `#num` 。</span><span class="sxs-lookup"><span data-stu-id="c3425-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="c3425-104">此錯誤有下列可能的原因：</span><span class="sxs-lookup"><span data-stu-id="c3425-104">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="c3425-105">嘗試將 `#num` 運算式轉換成序數失敗。</span><span class="sxs-lookup"><span data-stu-id="c3425-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
- <span data-ttu-id="c3425-106">`#num`指定的不會指定 DLL 中的任何函數。</span><span class="sxs-lookup"><span data-stu-id="c3425-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
- <span data-ttu-id="c3425-107">類型程式庫有不正確宣告，導致內部使用不正確序數。</span><span class="sxs-lookup"><span data-stu-id="c3425-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c3425-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c3425-108">To correct this error</span></span>  
  
1. <span data-ttu-id="c3425-109">請確定運算式代表有效的數位，或依名稱呼叫程式。</span><span class="sxs-lookup"><span data-stu-id="c3425-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2. <span data-ttu-id="c3425-110">請確定 `#num` 在 DLL 中找出有效的函式。</span><span class="sxs-lookup"><span data-stu-id="c3425-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3. <span data-ttu-id="c3425-111">將程式碼批註化，以找出造成問題的程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="c3425-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="c3425-112">撰寫 `Declare` 程式的語句，並將問題回報給類型程式庫廠商。</span><span class="sxs-lookup"><span data-stu-id="c3425-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3425-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3425-113">See also</span></span>

- [<span data-ttu-id="c3425-114">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="c3425-114">Declare Statement</span></span>](../statements/declare-statement.md)

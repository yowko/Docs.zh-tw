---
title: "無效的序數"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d31d0fba19cc16004c0b56786af30603d0c509ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="10219-102">無效的序數</span><span class="sxs-lookup"><span data-stu-id="10219-102">Ordinal is not valid</span></span>
<span data-ttu-id="10219-103">使用數字，而不是程序名稱，指示您動態連結程式庫 (DLL) 的呼叫使用`#num`語法。</span><span class="sxs-lookup"><span data-stu-id="10219-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="10219-104">此錯誤有下列可能原因：</span><span class="sxs-lookup"><span data-stu-id="10219-104">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="10219-105">嘗試將轉換`#num`無法為序數的運算式。</span><span class="sxs-lookup"><span data-stu-id="10219-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
-   <span data-ttu-id="10219-106">`#num`指定 DLL 中未指定任何函式。</span><span class="sxs-lookup"><span data-stu-id="10219-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
-   <span data-ttu-id="10219-107">類型程式庫有無效的宣告導致無效的序數數字的內部使用。</span><span class="sxs-lookup"><span data-stu-id="10219-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="10219-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="10219-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="10219-109">請確定運算式代表有效的數字，或呼叫程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="10219-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2.  <span data-ttu-id="10219-110">請確定`#num`識別 DLL 中是有效的函數。</span><span class="sxs-lookup"><span data-stu-id="10219-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3.  <span data-ttu-id="10219-111">找出造成問題，註解的程式碼的程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="10219-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="10219-112">寫入`Declare`程序，並回報問題類型程式庫的供應商的陳述式。</span><span class="sxs-lookup"><span data-stu-id="10219-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10219-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10219-113">See Also</span></span>  
 [<span data-ttu-id="10219-114">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="10219-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

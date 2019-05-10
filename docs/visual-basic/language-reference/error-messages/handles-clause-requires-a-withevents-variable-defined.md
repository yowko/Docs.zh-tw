---
title: Handles 子句需要 WithEvents 變數，該變數定義於包含類型或它的一種基底類型中
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: f119a4696334a93cf91bd859b502ff297aa33056
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662035"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a><span data-ttu-id="69991-102">Handles 子句需要 WithEvents 變數，該變數定義於包含類型或它的一種基底類型中</span><span class="sxs-lookup"><span data-stu-id="69991-102">Handles clause requires a WithEvents variable defined in the containing type or one of its base types</span></span>
<span data-ttu-id="69991-103">您並未提供`WithEvents`變數中您`Handles`子句。</span><span class="sxs-lookup"><span data-stu-id="69991-103">You did not supply a `WithEvents` variable in your `Handles` clause.</span></span> <span data-ttu-id="69991-104">`Handles`結尾的程序宣告關鍵字會導致以處理事件所使用宣告物件變數引發`WithEvents`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="69991-104">The `Handles` keyword at the end of a procedure declaration causes it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span>  
  
 <span data-ttu-id="69991-105">**錯誤 ID:** BC30506</span><span class="sxs-lookup"><span data-stu-id="69991-105">**Error ID:** BC30506</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="69991-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="69991-106">To correct this error</span></span>  
  
- <span data-ttu-id="69991-107">提供必要`WithEvents`變數。</span><span class="sxs-lookup"><span data-stu-id="69991-107">Supply the necessary `WithEvents` variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69991-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69991-108">See also</span></span>

- [<span data-ttu-id="69991-109">Handles</span><span class="sxs-lookup"><span data-stu-id="69991-109">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)

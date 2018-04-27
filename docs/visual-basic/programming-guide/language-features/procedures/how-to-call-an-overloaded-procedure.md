---
title: 如何：呼叫多載程序 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5eca03de6b6dd2ca2b992196b1ae224f8fbf5068
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="79b81-102">如何：呼叫多載程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79b81-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="79b81-103">多載化程序的優點是在呼叫的彈性。</span><span class="sxs-lookup"><span data-stu-id="79b81-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="79b81-104">呼叫程式碼可以取得傳遞至程序，然後再呼叫單一程序名稱，不論所傳遞的引數需要的資訊。</span><span class="sxs-lookup"><span data-stu-id="79b81-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="79b81-105">若要呼叫的程序具有多個定義的版本</span><span class="sxs-lookup"><span data-stu-id="79b81-105">To call a procedure that has more than one version defined</span></span>  
  
1.  <span data-ttu-id="79b81-106">在呼叫的程式碼，判斷哪些資料来傳遞至程序。</span><span class="sxs-lookup"><span data-stu-id="79b81-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2.  <span data-ttu-id="79b81-107">撰寫一般的方式，將資料呈現在引數清單的程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="79b81-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="79b81-108">請確定引數符合其中一個版本為程序定義中的參數清單。</span><span class="sxs-lookup"><span data-stu-id="79b81-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3.  <span data-ttu-id="79b81-109">您不需要判斷哪一個版本的程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="79b81-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="79b81-110">Visual Basic 會將控制項傳遞至比對引數清單的版本。</span><span class="sxs-lookup"><span data-stu-id="79b81-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="79b81-111">下列範例會呼叫`post`程序宣告中[如何： 定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="79b81-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="79b81-112">它會取得客戶識別，判斷它是否`String`或`Integer`，然後在任一情況下呼叫相同的程序。</span><span class="sxs-lookup"><span data-stu-id="79b81-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="79b81-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79b81-113">See Also</span></span>  
 [<span data-ttu-id="79b81-114">程序</span><span class="sxs-lookup"><span data-stu-id="79b81-114">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="79b81-115">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="79b81-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="79b81-116">程序多載化</span><span class="sxs-lookup"><span data-stu-id="79b81-116">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="79b81-117">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="79b81-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="79b81-118">如何：定義程序的多個版本</span><span class="sxs-lookup"><span data-stu-id="79b81-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="79b81-119">如何：使用選擇性參數的多載程序</span><span class="sxs-lookup"><span data-stu-id="79b81-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="79b81-120">如何：多載使用不確定參數數目的程序</span><span class="sxs-lookup"><span data-stu-id="79b81-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="79b81-121">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="79b81-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="79b81-122">多載解析</span><span class="sxs-lookup"><span data-stu-id="79b81-122">Overload Resolution</span></span>](./overload-resolution.md)  
 [<span data-ttu-id="79b81-123">多載</span><span class="sxs-lookup"><span data-stu-id="79b81-123">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)

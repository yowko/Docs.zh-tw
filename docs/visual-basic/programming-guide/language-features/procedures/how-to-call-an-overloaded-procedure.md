---
title: "如何︰ 呼叫多載程序 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, procedures
- procedures, overloading
- procedures, calling
- procedures, multiple versions
- procedure calls, overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 777df0cc81a4e0518773a0e8cc98d590d1c0cf0d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="5d8f6-102">如何：呼叫多載程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d8f6-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="5d8f6-103">多載化程序的優點是在呼叫的彈性。</span><span class="sxs-lookup"><span data-stu-id="5d8f6-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="5d8f6-104">呼叫程式碼可以取得的資訊，以便將傳遞至程序，然後呼叫單一程序名稱，不論所傳遞的引數。</span><span class="sxs-lookup"><span data-stu-id="5d8f6-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="5d8f6-105">呼叫已定義多個版本的程序</span><span class="sxs-lookup"><span data-stu-id="5d8f6-105">To call a procedure that has more than one version defined</span></span>  
  
1.  <span data-ttu-id="5d8f6-106">在呼叫的程式碼，判斷哪些資料来傳遞至程序。</span><span class="sxs-lookup"><span data-stu-id="5d8f6-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2.  <span data-ttu-id="5d8f6-107">以一般方式，將資料呈現在引數清單中撰寫的程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="5d8f6-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="5d8f6-108">請確定引數符合其中一個版本為程序定義中的參數清單。</span><span class="sxs-lookup"><span data-stu-id="5d8f6-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3.  <span data-ttu-id="5d8f6-109">您不需要以判斷要呼叫的程序的版本。</span><span class="sxs-lookup"><span data-stu-id="5d8f6-109">You do not have to determine which version of the procedure to call.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="5d8f6-110">將控制項傳遞到符合的引數清單的版本。</span><span class="sxs-lookup"><span data-stu-id="5d8f6-110"> passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="5d8f6-111">下列範例會呼叫`post`程序宣告於[How to︰ 定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="5d8f6-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="5d8f6-112">它會取得客戶識別碼、 判斷它是否為`String`或`Integer`，然後在任一情況下呼叫相同的程序。</span><span class="sxs-lookup"><span data-stu-id="5d8f6-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     <span data-ttu-id="5d8f6-113">[!code-vb[VbVbcnProcedures #&56;](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5d8f6-113">[!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]</span></span>  
  
     <span data-ttu-id="5d8f6-114">[!code-vb[VbVbcnProcedures #&57;](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5d8f6-114">[!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d8f6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d8f6-115">See Also</span></span>  
 <span data-ttu-id="5d8f6-116">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="5d8f6-116">[Procedures](./index.md) </span></span>  
<span data-ttu-id="5d8f6-117"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="5d8f6-117"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="5d8f6-118"> [多載化程序](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="5d8f6-118"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="5d8f6-119"> [疑難排解程序](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="5d8f6-119"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="5d8f6-120"> [如何︰ 定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="5d8f6-120"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="5d8f6-121"> [如何︰ 多載使用選擇性參數的程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="5d8f6-121"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="5d8f6-122"> [如何︰ 多載使用不定數目參數的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="5d8f6-122"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="5d8f6-123"> [多載化程序的考量](./considerations-in-overloading-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="5d8f6-123"> [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md) </span></span>  
<span data-ttu-id="5d8f6-124"> [多載解析](./overload-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="5d8f6-124"> [Overload Resolution](./overload-resolution.md) </span></span>  
<span data-ttu-id="5d8f6-125"> [多載](../../../../visual-basic/language-reference/modifiers/overloads.md)</span><span class="sxs-lookup"><span data-stu-id="5d8f6-125"> [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)</span></span>

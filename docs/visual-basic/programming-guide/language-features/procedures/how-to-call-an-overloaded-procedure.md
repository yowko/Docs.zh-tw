---
title: HOW TO：呼叫多載程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: d325c09516b4ce03facedce86f17ea49480b997a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666010"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="fcb1a-102">HOW TO：呼叫多載程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcb1a-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="fcb1a-103">多載化程序的優點是在呼叫的彈性。</span><span class="sxs-lookup"><span data-stu-id="fcb1a-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="fcb1a-104">呼叫端程式碼可以取得它需要傳遞至程序，並接著呼叫單一程序名稱，不論它傳遞引數的資訊。</span><span class="sxs-lookup"><span data-stu-id="fcb1a-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="fcb1a-105">呼叫已定義的多個版本的程序</span><span class="sxs-lookup"><span data-stu-id="fcb1a-105">To call a procedure that has more than one version defined</span></span>  
  
1. <span data-ttu-id="fcb1a-106">在呼叫的程式碼，判斷要傳遞至程序的資料。</span><span class="sxs-lookup"><span data-stu-id="fcb1a-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2. <span data-ttu-id="fcb1a-107">寫入程序呼叫一般的方式，將資料呈現在引數清單。</span><span class="sxs-lookup"><span data-stu-id="fcb1a-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="fcb1a-108">請確定引數符合其中一個版本的程序定義中的參數清單。</span><span class="sxs-lookup"><span data-stu-id="fcb1a-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3. <span data-ttu-id="fcb1a-109">您不必決定哪個版本的程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="fcb1a-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="fcb1a-110">Visual Basic 會將控制項傳遞至比對引數清單的版本。</span><span class="sxs-lookup"><span data-stu-id="fcb1a-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="fcb1a-111">下列範例會呼叫`post`程序宣告於[How to:定義多個版本的程序](./how-to-define-multiple-versions-of-a-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="fcb1a-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="fcb1a-112">它會取得客戶識別碼、 判斷是否`String`或`Integer`，然後在任一情況下呼叫相同的程序。</span><span class="sxs-lookup"><span data-stu-id="fcb1a-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="fcb1a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcb1a-113">See also</span></span>

- [<span data-ttu-id="fcb1a-114">程序</span><span class="sxs-lookup"><span data-stu-id="fcb1a-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="fcb1a-115">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="fcb1a-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="fcb1a-116">程序多載化</span><span class="sxs-lookup"><span data-stu-id="fcb1a-116">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="fcb1a-117">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="fcb1a-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="fcb1a-118">如何：定義多個版本的程序</span><span class="sxs-lookup"><span data-stu-id="fcb1a-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="fcb1a-119">如何：多載會採用選擇性參數的程序</span><span class="sxs-lookup"><span data-stu-id="fcb1a-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="fcb1a-120">如何：多載不定數目參數的程序</span><span class="sxs-lookup"><span data-stu-id="fcb1a-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="fcb1a-121">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="fcb1a-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="fcb1a-122">多載解析</span><span class="sxs-lookup"><span data-stu-id="fcb1a-122">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="fcb1a-123">多載</span><span class="sxs-lookup"><span data-stu-id="fcb1a-123">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)

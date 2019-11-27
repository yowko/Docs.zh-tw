---
title: 如何：呼叫多載程序
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: d983f5f6183c33141079ed35171f7a73f254450f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340200"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="cb134-102">如何：呼叫多載程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb134-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="cb134-103">多載程式的優點是呼叫的彈性。</span><span class="sxs-lookup"><span data-stu-id="cb134-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="cb134-104">呼叫程式碼可以取得傳遞至程式所需的資訊，然後呼叫單一程式名稱，而不論其傳遞的引數為何。</span><span class="sxs-lookup"><span data-stu-id="cb134-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="cb134-105">呼叫已定義一個以上版本的程式</span><span class="sxs-lookup"><span data-stu-id="cb134-105">To call a procedure that has more than one version defined</span></span>  
  
1. <span data-ttu-id="cb134-106">在呼叫程式碼中，判斷要傳遞給程式的資料。</span><span class="sxs-lookup"><span data-stu-id="cb134-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2. <span data-ttu-id="cb134-107">以一般方式撰寫程序呼叫，並在引數清單中呈現資料。</span><span class="sxs-lookup"><span data-stu-id="cb134-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="cb134-108">請確定引數符合為程式定義的其中一個版本中的參數清單。</span><span class="sxs-lookup"><span data-stu-id="cb134-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3. <span data-ttu-id="cb134-109">您不需要決定要呼叫的程式版本。</span><span class="sxs-lookup"><span data-stu-id="cb134-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="cb134-110">Visual Basic 會將控制權傳遞至符合引數清單的版本。</span><span class="sxs-lookup"><span data-stu-id="cb134-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="cb134-111">下列範例會呼叫[如何：定義程式的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)中所宣告的 `post` 程式。</span><span class="sxs-lookup"><span data-stu-id="cb134-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="cb134-112">它會取得客戶識別、判斷其是否為 `String` 或 `Integer`，然後在任一情況下呼叫相同的程式。</span><span class="sxs-lookup"><span data-stu-id="cb134-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="cb134-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="cb134-113">See also</span></span>

- [<span data-ttu-id="cb134-114">程序</span><span class="sxs-lookup"><span data-stu-id="cb134-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="cb134-115">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="cb134-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="cb134-116">程序多載化</span><span class="sxs-lookup"><span data-stu-id="cb134-116">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="cb134-117">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="cb134-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="cb134-118">如何：定義程序的多個版本</span><span class="sxs-lookup"><span data-stu-id="cb134-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="cb134-119">如何：使用選擇性參數的多載程序</span><span class="sxs-lookup"><span data-stu-id="cb134-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="cb134-120">如何：多載使用不確定參數數目的程序</span><span class="sxs-lookup"><span data-stu-id="cb134-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="cb134-121">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="cb134-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="cb134-122">多載解析</span><span class="sxs-lookup"><span data-stu-id="cb134-122">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="cb134-123">多載</span><span class="sxs-lookup"><span data-stu-id="cb134-123">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)

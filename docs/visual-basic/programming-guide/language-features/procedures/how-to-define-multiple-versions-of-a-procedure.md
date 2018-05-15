---
title: 如何：定義程序的多個版本 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: a4d0c5bbb07dd5433ff62179fc10a6274bf19364
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="88746-102">如何：定義程序的多個版本 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88746-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="88746-103">您可以定義程序中由多個版本*多載*它使用相同名稱但不同的參數清單，每個版本。</span><span class="sxs-lookup"><span data-stu-id="88746-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="88746-104">多載的用途是定義程序的數個密切相關的版本，而不需要加以區分名稱。</span><span class="sxs-lookup"><span data-stu-id="88746-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="88746-105">如需詳細資訊，請參閱[程序多載](./procedure-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="88746-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="88746-106">若要定義多個版本的程序</span><span class="sxs-lookup"><span data-stu-id="88746-106">To define multiple versions of a procedure</span></span>  
  
1.  <span data-ttu-id="88746-107">寫入`Sub`或`Function`您想要定義的程序的每個版本的宣告陳述式。</span><span class="sxs-lookup"><span data-stu-id="88746-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="88746-108">每個宣告中使用相同的程序名稱。</span><span class="sxs-lookup"><span data-stu-id="88746-108">Use the same procedure name in every declaration.</span></span>  
  
2.  <span data-ttu-id="88746-109">在前面`Sub`或`Function`關鍵字與每個宣告中的[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="88746-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="88746-110">您可以選擇性地省略`Overloads`在宣告中，但包含在任何宣告，必須將它包含在每個宣告中。</span><span class="sxs-lookup"><span data-stu-id="88746-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3.  <span data-ttu-id="88746-111">每個宣告陳述式後面，撰寫程序程式碼以處理呼叫的程式碼提供的比對該版本的參數清單的引數的特定情況。</span><span class="sxs-lookup"><span data-stu-id="88746-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="88746-112">您不必測試呼叫的程式碼已提供的參數。</span><span class="sxs-lookup"><span data-stu-id="88746-112">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="88746-113">Visual Basic 會將控制項傳遞至程序的版本相符。</span><span class="sxs-lookup"><span data-stu-id="88746-113">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4.  <span data-ttu-id="88746-114">終止與程序的每個版本`End Sub`或`End Function`視陳述式。</span><span class="sxs-lookup"><span data-stu-id="88746-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88746-115">範例</span><span class="sxs-lookup"><span data-stu-id="88746-115">Example</span></span>  
 <span data-ttu-id="88746-116">下列範例會定義`Sub`張貼客戶餘額一筆交易的程序。</span><span class="sxs-lookup"><span data-stu-id="88746-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="88746-117">它會使用`Overloads`關鍵字來定義兩個版本的程序，一次可接受依名稱和其他客戶的帳戶號碼。</span><span class="sxs-lookup"><span data-stu-id="88746-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 <span data-ttu-id="88746-118">呼叫程式碼可以取得客戶識別為`String`或`Integer`，然後在任一情況下使用相同的呼叫陳述式。</span><span class="sxs-lookup"><span data-stu-id="88746-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="88746-119">如需有關如何呼叫這些版本資訊`post`程序，請參閱[如何： 呼叫多載程序](./how-to-call-an-overloaded-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="88746-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="88746-120">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="88746-120">Compiling the Code</span></span>  
 <span data-ttu-id="88746-121">請確定每個多載版本都有相同的程序名稱，但不同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="88746-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88746-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88746-122">See Also</span></span>  
 [<span data-ttu-id="88746-123">程序</span><span class="sxs-lookup"><span data-stu-id="88746-123">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="88746-124">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="88746-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="88746-125">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="88746-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="88746-126">如何：使用選擇性參數的多載程序</span><span class="sxs-lookup"><span data-stu-id="88746-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="88746-127">如何：多載使用不確定參數數目的程序</span><span class="sxs-lookup"><span data-stu-id="88746-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="88746-128">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="88746-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="88746-129">多載解析</span><span class="sxs-lookup"><span data-stu-id="88746-129">Overload Resolution</span></span>](./overload-resolution.md)

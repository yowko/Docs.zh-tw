---
title: HOW TO：定義多個版本的程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: fc7a8e18394b904f0c22a80f71dee091d4f786ab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59324028"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="b3600-102">HOW TO：定義多個版本的程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3600-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="b3600-103">您可以在多個版本中所定義的程序*多載*它針對每個版本使用相同名稱但不同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="b3600-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="b3600-104">多載的用途是定義程序的數個密切相關的版本，而不需要依名稱加以區隔。</span><span class="sxs-lookup"><span data-stu-id="b3600-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="b3600-105">如需詳細資訊，請參閱 [Procedure Overloading](./procedure-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="b3600-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="b3600-106">若要定義多個版本的程序</span><span class="sxs-lookup"><span data-stu-id="b3600-106">To define multiple versions of a procedure</span></span>  
  
1. <span data-ttu-id="b3600-107">撰寫`Sub`或`Function`宣告陳述式，針對您想要定義的程序的每個版本。</span><span class="sxs-lookup"><span data-stu-id="b3600-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="b3600-108">在每個宣告中使用相同的程序名稱。</span><span class="sxs-lookup"><span data-stu-id="b3600-108">Use the same procedure name in every declaration.</span></span>  
  
2. <span data-ttu-id="b3600-109">在前面`Sub`或是`Function`在每個宣告中的關鍵字[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b3600-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="b3600-110">您可以選擇性地省略`Overloads`在宣告中，但包含在任何宣告，您必須將它包含在每個宣告。</span><span class="sxs-lookup"><span data-stu-id="b3600-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3. <span data-ttu-id="b3600-111">每個宣告陳述式後面，撰寫程序程式碼以處理呼叫的程式碼提供的比對該版本的參數清單的引數的特定情況。</span><span class="sxs-lookup"><span data-stu-id="b3600-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="b3600-112">您不必測試呼叫程式碼已提供的參數。</span><span class="sxs-lookup"><span data-stu-id="b3600-112">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="b3600-113">Visual Basic 會將控制項傳遞至您的程序版本相符。</span><span class="sxs-lookup"><span data-stu-id="b3600-113">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4. <span data-ttu-id="b3600-114">終止此程序的每個版本`End Sub`或`End Function`適當的陳述式。</span><span class="sxs-lookup"><span data-stu-id="b3600-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3600-115">範例</span><span class="sxs-lookup"><span data-stu-id="b3600-115">Example</span></span>  
 <span data-ttu-id="b3600-116">下列範例會定義`Sub`張貼對客戶的餘額交易的程序。</span><span class="sxs-lookup"><span data-stu-id="b3600-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="b3600-117">它會使用`Overloads`關鍵字來定義兩個版本的程序，可接受由名稱和其他客戶的帳戶號碼。</span><span class="sxs-lookup"><span data-stu-id="b3600-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 <span data-ttu-id="b3600-118">呼叫端程式碼可以取得客戶識別為`String`或`Integer`，然後在任一情況下使用相同的呼叫陳述式。</span><span class="sxs-lookup"><span data-stu-id="b3600-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="b3600-119">如需如何呼叫這些版本資訊`post`程序，請參閱[How to:呼叫多載程序](./how-to-call-an-overloaded-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="b3600-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b3600-120">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b3600-120">Compiling the Code</span></span>  
 <span data-ttu-id="b3600-121">請確定每個多載的版本具有相同的程序名稱，但有不同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="b3600-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3600-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3600-122">See also</span></span>

- [<span data-ttu-id="b3600-123">程序</span><span class="sxs-lookup"><span data-stu-id="b3600-123">Procedures</span></span>](./index.md)
- [<span data-ttu-id="b3600-124">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="b3600-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b3600-125">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="b3600-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="b3600-126">如何：多載會採用選擇性參數的程序</span><span class="sxs-lookup"><span data-stu-id="b3600-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="b3600-127">如何：多載不定數目參數的程序</span><span class="sxs-lookup"><span data-stu-id="b3600-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="b3600-128">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="b3600-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="b3600-129">多載解析</span><span class="sxs-lookup"><span data-stu-id="b3600-129">Overload Resolution</span></span>](./overload-resolution.md)

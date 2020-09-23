---
title: 如何：定義程序的多個版本
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: 2661603ba33dd0bc28ac1a192794a4534225b641
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071634"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="f63d9-102">如何：定義程序的多個版本 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f63d9-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>

<span data-ttu-id="f63d9-103">您可以使用相同的名稱，但針對每個版本使用不同的參數清單，在多個版本中*定義程式。*</span><span class="sxs-lookup"><span data-stu-id="f63d9-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="f63d9-104">多載的目的是要定義多個密切相關的程式版本，而不需要依名稱來區分。</span><span class="sxs-lookup"><span data-stu-id="f63d9-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="f63d9-105">如需詳細資訊，請參閱 [Procedure Overloading](./procedure-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="f63d9-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="f63d9-106">若要定義程式的多個版本</span><span class="sxs-lookup"><span data-stu-id="f63d9-106">To define multiple versions of a procedure</span></span>  
  
1. <span data-ttu-id="f63d9-107">`Sub` `Function` 針對您要定義的每個程式版本，撰寫或宣告語句。</span><span class="sxs-lookup"><span data-stu-id="f63d9-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="f63d9-108">在每個宣告中使用相同的程式名稱。</span><span class="sxs-lookup"><span data-stu-id="f63d9-108">Use the same procedure name in every declaration.</span></span>  
  
2. <span data-ttu-id="f63d9-109">`Sub`在每個宣告中的或關鍵字之前加上 `Function` [Overloads](../../../language-reference/modifiers/overloads.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f63d9-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="f63d9-110">您可以選擇性地在宣告中省略 `Overloads` ，但如果您將它包含在任何宣告中，則必須將它包含在每個宣告中。</span><span class="sxs-lookup"><span data-stu-id="f63d9-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3. <span data-ttu-id="f63d9-111">在每個宣告語句之後，撰寫程式程式碼來處理特定案例，其中呼叫程式碼會提供符合該版本參數清單的引數。</span><span class="sxs-lookup"><span data-stu-id="f63d9-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="f63d9-112">您不需要測試呼叫程式碼提供的參數。</span><span class="sxs-lookup"><span data-stu-id="f63d9-112">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="f63d9-113">Visual Basic 將控制權傳遞給程式的相符版本。</span><span class="sxs-lookup"><span data-stu-id="f63d9-113">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4. <span data-ttu-id="f63d9-114">`End Sub`請視需要使用或語句來終止程式的每個版本 `End Function` 。</span><span class="sxs-lookup"><span data-stu-id="f63d9-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f63d9-115">範例</span><span class="sxs-lookup"><span data-stu-id="f63d9-115">Example</span></span>  

 <span data-ttu-id="f63d9-116">下列範例會定義將 `Sub` 交易張貼至客戶餘額的程式。</span><span class="sxs-lookup"><span data-stu-id="f63d9-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="f63d9-117">它會使用 `Overloads` 關鍵字來定義程式的兩個版本，一個是依名稱接受客戶，另一個則依據帳戶編號。</span><span class="sxs-lookup"><span data-stu-id="f63d9-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 <span data-ttu-id="f63d9-118">呼叫程式碼可以將客戶識別取得為 `String` 或 `Integer` ，然後在任何一種情況下使用相同的呼叫語句。</span><span class="sxs-lookup"><span data-stu-id="f63d9-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="f63d9-119">如需如何呼叫這些程式版本的詳細資訊 `post` ，請參閱 [如何：呼叫](./how-to-call-an-overloaded-procedure.md)多載程式。</span><span class="sxs-lookup"><span data-stu-id="f63d9-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="f63d9-120">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f63d9-120">Compile the code</span></span>  

 <span data-ttu-id="f63d9-121">請確定每個多載版本都有相同的程式名稱，但有不同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="f63d9-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f63d9-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f63d9-122">See also</span></span>

- [<span data-ttu-id="f63d9-123">程序</span><span class="sxs-lookup"><span data-stu-id="f63d9-123">Procedures</span></span>](./index.md)
- [<span data-ttu-id="f63d9-124">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="f63d9-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f63d9-125">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="f63d9-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="f63d9-126">如何：使用選擇性參數的多載程序</span><span class="sxs-lookup"><span data-stu-id="f63d9-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="f63d9-127">如何：多載使用不確定參數數目的程序</span><span class="sxs-lookup"><span data-stu-id="f63d9-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="f63d9-128">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="f63d9-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="f63d9-129">多載解析</span><span class="sxs-lookup"><span data-stu-id="f63d9-129">Overload Resolution</span></span>](./overload-resolution.md)

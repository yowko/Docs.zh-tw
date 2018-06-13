---
title: 程序多載化 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 0d1f2c4d8c88922659b3d91ed41d5e760e6e5233
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653910"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="f2d9e-102">程序多載化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2d9e-102">Procedure Overloading (Visual Basic)</span></span>
<span data-ttu-id="f2d9e-103">*多載*程序會表示定義在多個版本中，使用相同名稱但不同參數清單。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="f2d9e-104">多載的用途是定義程序的數個密切相關的版本，而不需要加以區分名稱。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="f2d9e-105">您可以不同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-105">You do this by varying the parameter list.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="f2d9e-106">多載規則</span><span class="sxs-lookup"><span data-stu-id="f2d9e-106">Overloading Rules</span></span>  
 <span data-ttu-id="f2d9e-107">當您多載程序時，適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="f2d9e-107">When you overload a procedure, the following rules apply:</span></span>  
  
-   <span data-ttu-id="f2d9e-108">**相同名稱**。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-108">**Same Name**.</span></span> <span data-ttu-id="f2d9e-109">每個多載的版本必須使用相同的程序名稱。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-109">Each overloaded version must use the same procedure name.</span></span>  
  
-   <span data-ttu-id="f2d9e-110">**不同的簽章**。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-110">**Different Signature**.</span></span> <span data-ttu-id="f2d9e-111">每個多載的版本必須與所有其他多載版本中至少一個下列方面不同：</span><span class="sxs-lookup"><span data-stu-id="f2d9e-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>  
  
    -   <span data-ttu-id="f2d9e-112">參數數目</span><span class="sxs-lookup"><span data-stu-id="f2d9e-112">Number of parameters</span></span>  
  
    -   <span data-ttu-id="f2d9e-113">參數的順序</span><span class="sxs-lookup"><span data-stu-id="f2d9e-113">Order of the parameters</span></span>  
  
    -   <span data-ttu-id="f2d9e-114">參數的資料類型</span><span class="sxs-lookup"><span data-stu-id="f2d9e-114">Data types of the parameters</span></span>  
  
    -   <span data-ttu-id="f2d9e-115">（適用於泛型程序） 的型別參數數目</span><span class="sxs-lookup"><span data-stu-id="f2d9e-115">Number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="f2d9e-116">（僅適用於轉換運算子） 的傳回型別</span><span class="sxs-lookup"><span data-stu-id="f2d9e-116">Return type (only for a conversion operator)</span></span>  
  
     <span data-ttu-id="f2d9e-117">統稱為 「 程序名稱，以及先前的項目*簽章*程序。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="f2d9e-118">當您呼叫多載的程序時，編譯器會用來檢查呼叫正確符合定義的簽章。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>  
  
-   <span data-ttu-id="f2d9e-119">**項目不屬於簽章**。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="f2d9e-120">您無法多載程序，而不改變簽章。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="f2d9e-121">特別是，您無法只改變一個或多個下列項目來多載程序：</span><span class="sxs-lookup"><span data-stu-id="f2d9e-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>  
  
    -   <span data-ttu-id="f2d9e-122">程序修飾詞關鍵字，例如`Public`， `Shared`，和 `Static`</span><span class="sxs-lookup"><span data-stu-id="f2d9e-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>  
  
    -   <span data-ttu-id="f2d9e-123">參數或型別參數名稱</span><span class="sxs-lookup"><span data-stu-id="f2d9e-123">Parameter or type parameter names</span></span>  
  
    -   <span data-ttu-id="f2d9e-124">類型參數條件約束 （適用於泛型程序）</span><span class="sxs-lookup"><span data-stu-id="f2d9e-124">Type parameter constraints (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="f2d9e-125">參數修飾詞關鍵字，例如`ByRef`和 `Optional`</span><span class="sxs-lookup"><span data-stu-id="f2d9e-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>  
  
    -   <span data-ttu-id="f2d9e-126">傳回值</span><span class="sxs-lookup"><span data-stu-id="f2d9e-126">Whether it returns a value</span></span>  
  
    -   <span data-ttu-id="f2d9e-127">傳回值 （除了轉換運算子） 的資料類型</span><span class="sxs-lookup"><span data-stu-id="f2d9e-127">The data type of the return value (except for a conversion operator)</span></span>  
  
     <span data-ttu-id="f2d9e-128">上述清單中的項目不是簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="f2d9e-129">雖然您無法使用它們來區別多載版本，您可以將它們異正確簽章來區分的多載版本。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>  
  
-   <span data-ttu-id="f2d9e-130">**晚期繫結引數**。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="f2d9e-131">如果您想要將晚期繫結的物件變數傳遞給一個多載版本，您必須宣告適當的參數為<xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>  
  
## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="f2d9e-132">多個版本的程序</span><span class="sxs-lookup"><span data-stu-id="f2d9e-132">Multiple Versions of a Procedure</span></span>  
 <span data-ttu-id="f2d9e-133">假設您要撰寫`Sub`程序以公佈交易中針對客戶的平衡，而您想要能夠依名稱或帳戶是指客戶。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="f2d9e-134">若要做到這一點，您可以定義兩個不同`Sub`程序，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f2d9e-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#73](./codesnippet/VisualBasic/procedure-overloading_1.vb)]  
  
### <a name="overloaded-versions"></a><span data-ttu-id="f2d9e-135">多載的版本</span><span class="sxs-lookup"><span data-stu-id="f2d9e-135">Overloaded Versions</span></span>  
 <span data-ttu-id="f2d9e-136">替代方法是將多載的單一程序名稱。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-136">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="f2d9e-137">您可以使用[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字來定義為每個參數清單中，程序的版本，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f2d9e-137">You can use the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/procedure-overloading_2.vb)]  
  
#### <a name="additional-overloads"></a><span data-ttu-id="f2d9e-138">其他多載</span><span class="sxs-lookup"><span data-stu-id="f2d9e-138">Additional Overloads</span></span>  
 <span data-ttu-id="f2d9e-139">如果您也想要接受在交易量`Decimal`或`Single`，您無法進一步多載`post`以便進行這項差異。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="f2d9e-140">如果您已將每個在上述範例中的多載有四個`Sub`程序有相同的名稱，但具有四個不同的簽章。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>  
  
## <a name="advantages-of-overloading"></a><span data-ttu-id="f2d9e-141">多載的優點</span><span class="sxs-lookup"><span data-stu-id="f2d9e-141">Advantages of Overloading</span></span>  
 <span data-ttu-id="f2d9e-142">多載化程序的優點是在呼叫的彈性。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-142">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="f2d9e-143">若要使用`post`程序宣告在上述範例中，呼叫程式碼可以取得客戶識別為`String`或`Integer`，然後在任一情況下呼叫相同的程序。</span><span class="sxs-lookup"><span data-stu-id="f2d9e-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="f2d9e-144">下面這個範例可說明這點：</span><span class="sxs-lookup"><span data-stu-id="f2d9e-144">The following example illustrates this:</span></span>  
  
 [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/procedure-overloading_3.vb)]  
  
 [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/procedure-overloading_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f2d9e-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2d9e-145">See Also</span></span>  
 [<span data-ttu-id="f2d9e-146">程序</span><span class="sxs-lookup"><span data-stu-id="f2d9e-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="f2d9e-147">如何：定義程序的多個版本</span><span class="sxs-lookup"><span data-stu-id="f2d9e-147">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="f2d9e-148">如何：呼叫多載程序</span><span class="sxs-lookup"><span data-stu-id="f2d9e-148">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="f2d9e-149">如何：使用選擇性參數的多載程序</span><span class="sxs-lookup"><span data-stu-id="f2d9e-149">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="f2d9e-150">如何：多載使用不確定參數數目的程序</span><span class="sxs-lookup"><span data-stu-id="f2d9e-150">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="f2d9e-151">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="f2d9e-151">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="f2d9e-152">多載解析</span><span class="sxs-lookup"><span data-stu-id="f2d9e-152">Overload Resolution</span></span>](./overload-resolution.md)  
 [<span data-ttu-id="f2d9e-153">多載</span><span class="sxs-lookup"><span data-stu-id="f2d9e-153">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="f2d9e-154">Visual Basic 中的泛型型別</span><span class="sxs-lookup"><span data-stu-id="f2d9e-154">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

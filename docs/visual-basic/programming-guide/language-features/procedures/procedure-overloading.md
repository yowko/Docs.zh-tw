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
ms.openlocfilehash: 6e8d1fa72c60c4fa3d2237ad24c2d1b4891a7bf2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828234"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="4e672-102">程序多載化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e672-102">Procedure Overloading (Visual Basic)</span></span>
<span data-ttu-id="4e672-103">*多載*程序可讓您表示定義在多個版本中，使用相同名稱但不同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="4e672-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="4e672-104">多載的用途是定義程序的數個密切相關的版本，而不需要依名稱加以區隔。</span><span class="sxs-lookup"><span data-stu-id="4e672-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="4e672-105">您可以不同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="4e672-105">You do this by varying the parameter list.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="4e672-106">多載規則</span><span class="sxs-lookup"><span data-stu-id="4e672-106">Overloading Rules</span></span>  
 <span data-ttu-id="4e672-107">當您多載程序時，適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="4e672-107">When you overload a procedure, the following rules apply:</span></span>  
  
-   <span data-ttu-id="4e672-108">**相同名稱**。</span><span class="sxs-lookup"><span data-stu-id="4e672-108">**Same Name**.</span></span> <span data-ttu-id="4e672-109">每個多載的版本必須使用相同的程序名稱。</span><span class="sxs-lookup"><span data-stu-id="4e672-109">Each overloaded version must use the same procedure name.</span></span>  
  
-   <span data-ttu-id="4e672-110">**不同的簽章**。</span><span class="sxs-lookup"><span data-stu-id="4e672-110">**Different Signature**.</span></span> <span data-ttu-id="4e672-111">每個多載的版本必須與所有其他多載版本至少要有一個下列方面不同：</span><span class="sxs-lookup"><span data-stu-id="4e672-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>  
  
    -   <span data-ttu-id="4e672-112">參數數目</span><span class="sxs-lookup"><span data-stu-id="4e672-112">Number of parameters</span></span>  
  
    -   <span data-ttu-id="4e672-113">參數的順序</span><span class="sxs-lookup"><span data-stu-id="4e672-113">Order of the parameters</span></span>  
  
    -   <span data-ttu-id="4e672-114">參數的資料類型</span><span class="sxs-lookup"><span data-stu-id="4e672-114">Data types of the parameters</span></span>  
  
    -   <span data-ttu-id="4e672-115">（適用於泛型程序） 的型別參數數目</span><span class="sxs-lookup"><span data-stu-id="4e672-115">Number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="4e672-116">（僅適用於轉換運算子） 的傳回型別</span><span class="sxs-lookup"><span data-stu-id="4e672-116">Return type (only for a conversion operator)</span></span>  
  
     <span data-ttu-id="4e672-117">統稱為程序名稱，連同上述項目*簽章*程序。</span><span class="sxs-lookup"><span data-stu-id="4e672-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="4e672-118">當您呼叫多載的程序時，編譯器會用來檢查呼叫正確地符合定義的簽章。</span><span class="sxs-lookup"><span data-stu-id="4e672-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>  
  
-   <span data-ttu-id="4e672-119">**項目不屬於簽章**。</span><span class="sxs-lookup"><span data-stu-id="4e672-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="4e672-120">您無法多載程序，而不需要不同的簽章。</span><span class="sxs-lookup"><span data-stu-id="4e672-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="4e672-121">特別是，您無法只改變一個或多個下列項目來多載程序：</span><span class="sxs-lookup"><span data-stu-id="4e672-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>  
  
    -   <span data-ttu-id="4e672-122">程序修飾詞關鍵字，例如`Public`， `Shared`，及 `Static`</span><span class="sxs-lookup"><span data-stu-id="4e672-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>  
  
    -   <span data-ttu-id="4e672-123">參數或型別參數名稱</span><span class="sxs-lookup"><span data-stu-id="4e672-123">Parameter or type parameter names</span></span>  
  
    -   <span data-ttu-id="4e672-124">（適用於泛型程序） 的類型參數條件約束</span><span class="sxs-lookup"><span data-stu-id="4e672-124">Type parameter constraints (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="4e672-125">參數修飾詞關鍵字，例如`ByRef`和 `Optional`</span><span class="sxs-lookup"><span data-stu-id="4e672-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>  
  
    -   <span data-ttu-id="4e672-126">是否會傳回值</span><span class="sxs-lookup"><span data-stu-id="4e672-126">Whether it returns a value</span></span>  
  
    -   <span data-ttu-id="4e672-127">傳回值 （除了轉換運算子） 的資料類型</span><span class="sxs-lookup"><span data-stu-id="4e672-127">The data type of the return value (except for a conversion operator)</span></span>  
  
     <span data-ttu-id="4e672-128">上述清單中的項目不是簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="4e672-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="4e672-129">雖然您無法使用它們來區別多載版本，您可以將它們異適當地加以區分它們的簽章的多載版本。</span><span class="sxs-lookup"><span data-stu-id="4e672-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>  
  
-   <span data-ttu-id="4e672-130">**晚期繫結引數**。</span><span class="sxs-lookup"><span data-stu-id="4e672-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="4e672-131">如果您想要將晚期繫結的物件變數傳遞給的多載版本，您必須宣告適當的參數為<xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="4e672-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>  
  
## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="4e672-132">多個版本的程序</span><span class="sxs-lookup"><span data-stu-id="4e672-132">Multiple Versions of a Procedure</span></span>  
 <span data-ttu-id="4e672-133">假設您正在撰寫`Sub`程序來張貼交易中的針對客戶餘額，以及您想要能夠依名稱或帳戶，請參閱給客戶。</span><span class="sxs-lookup"><span data-stu-id="4e672-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="4e672-134">若要做到這一點，您可以定義兩個不同`Sub`程序，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4e672-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]  
  
### <a name="overloaded-versions"></a><span data-ttu-id="4e672-135">多載的版本</span><span class="sxs-lookup"><span data-stu-id="4e672-135">Overloaded Versions</span></span>  
 <span data-ttu-id="4e672-136">替代方法是多載是單一的程序名稱。</span><span class="sxs-lookup"><span data-stu-id="4e672-136">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="4e672-137">您可以使用[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字來定義每個參數清單，此程序的版本，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4e672-137">You can use the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
#### <a name="additional-overloads"></a><span data-ttu-id="4e672-138">其他多載</span><span class="sxs-lookup"><span data-stu-id="4e672-138">Additional Overloads</span></span>  
 <span data-ttu-id="4e672-139">如果您也想要接受在交易量`Decimal`或是`Single`，您可以進一步多載`post`以便進行這項差異。</span><span class="sxs-lookup"><span data-stu-id="4e672-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="4e672-140">如果您這麼做會以每個多載，在上述範例中，有四個`Sub`程序，所有具有相同名稱但具有四個不同的簽章。</span><span class="sxs-lookup"><span data-stu-id="4e672-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>  
  
## <a name="advantages-of-overloading"></a><span data-ttu-id="4e672-141">多載的優點</span><span class="sxs-lookup"><span data-stu-id="4e672-141">Advantages of Overloading</span></span>  
 <span data-ttu-id="4e672-142">多載化程序的優點是在呼叫的彈性。</span><span class="sxs-lookup"><span data-stu-id="4e672-142">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="4e672-143">若要使用`post`程序的宣告是在上述範例中，而呼叫的程式碼可以取得客戶識別為`String`或`Integer`，然後在任一情況下呼叫相同的程序。</span><span class="sxs-lookup"><span data-stu-id="4e672-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="4e672-144">下面這個範例可說明這點：</span><span class="sxs-lookup"><span data-stu-id="4e672-144">The following example illustrates this:</span></span>  
  
 [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
 [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="4e672-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e672-145">See also</span></span>

- [<span data-ttu-id="4e672-146">程序</span><span class="sxs-lookup"><span data-stu-id="4e672-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="4e672-147">如何：定義多個版本的程序</span><span class="sxs-lookup"><span data-stu-id="4e672-147">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="4e672-148">如何：呼叫多載程序</span><span class="sxs-lookup"><span data-stu-id="4e672-148">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="4e672-149">如何：多載會採用選擇性參數的程序</span><span class="sxs-lookup"><span data-stu-id="4e672-149">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="4e672-150">如何：多載不定數目參數的程序</span><span class="sxs-lookup"><span data-stu-id="4e672-150">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="4e672-151">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="4e672-151">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="4e672-152">多載解析</span><span class="sxs-lookup"><span data-stu-id="4e672-152">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="4e672-153">多載</span><span class="sxs-lookup"><span data-stu-id="4e672-153">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="4e672-154">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4e672-154">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

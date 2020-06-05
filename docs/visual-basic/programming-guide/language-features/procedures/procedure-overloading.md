---
title: 程序多載
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
ms.openlocfilehash: f8accc74fbdd9b1d8cf9bc3d8f6ddd26f73452b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363872"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="ec37e-102">程序多載化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec37e-102">Procedure Overloading (Visual Basic)</span></span>

<span data-ttu-id="ec37e-103">*Overloading*多載程式表示使用相同名稱但不同的參數清單，在多個版本中定義它。</span><span class="sxs-lookup"><span data-stu-id="ec37e-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="ec37e-104">多載的目的是要定義程式的數個緊密相關版本，而不需要依名稱區分。</span><span class="sxs-lookup"><span data-stu-id="ec37e-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="ec37e-105">您可以藉由改變參數清單來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="ec37e-105">You do this by varying the parameter list.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="ec37e-106">多載規則</span><span class="sxs-lookup"><span data-stu-id="ec37e-106">Overloading Rules</span></span>

<span data-ttu-id="ec37e-107">當您多載程式時，適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="ec37e-107">When you overload a procedure, the following rules apply:</span></span>

- <span data-ttu-id="ec37e-108">**相同名稱**。</span><span class="sxs-lookup"><span data-stu-id="ec37e-108">**Same Name**.</span></span> <span data-ttu-id="ec37e-109">每個多載的版本都必須使用相同的程式名稱。</span><span class="sxs-lookup"><span data-stu-id="ec37e-109">Each overloaded version must use the same procedure name.</span></span>

- <span data-ttu-id="ec37e-110">**不同**的簽章。</span><span class="sxs-lookup"><span data-stu-id="ec37e-110">**Different Signature**.</span></span> <span data-ttu-id="ec37e-111">每個多載的版本都必須與所有其他多載版本的差異，至少為下列其中一個方面：</span><span class="sxs-lookup"><span data-stu-id="ec37e-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>

  - <span data-ttu-id="ec37e-112">參數數目</span><span class="sxs-lookup"><span data-stu-id="ec37e-112">Number of parameters</span></span>

  - <span data-ttu-id="ec37e-113">參數的順序</span><span class="sxs-lookup"><span data-stu-id="ec37e-113">Order of the parameters</span></span>

  - <span data-ttu-id="ec37e-114">參數的資料類型</span><span class="sxs-lookup"><span data-stu-id="ec37e-114">Data types of the parameters</span></span>

  - <span data-ttu-id="ec37e-115">型別參數的數目（適用于泛型程式）</span><span class="sxs-lookup"><span data-stu-id="ec37e-115">Number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="ec37e-116">傳回類型（僅適用于轉換運算子）</span><span class="sxs-lookup"><span data-stu-id="ec37e-116">Return type (only for a conversion operator)</span></span>

  <span data-ttu-id="ec37e-117">加上程式名稱，前面的專案統稱為*程式的簽*章。</span><span class="sxs-lookup"><span data-stu-id="ec37e-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="ec37e-118">當您呼叫多載程式時，編譯器會使用簽章來檢查呼叫是否正確符合定義。</span><span class="sxs-lookup"><span data-stu-id="ec37e-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>

- <span data-ttu-id="ec37e-119">**專案不是簽章的一部分**。</span><span class="sxs-lookup"><span data-stu-id="ec37e-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="ec37e-120">您無法多載程式，而不會改變簽章。</span><span class="sxs-lookup"><span data-stu-id="ec37e-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="ec37e-121">特別的是，您無法藉由只改變下列一個或多個專案，來多載程式：</span><span class="sxs-lookup"><span data-stu-id="ec37e-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>

  - <span data-ttu-id="ec37e-122">程式修飾詞關鍵字，例如 `Public` 、 `Shared` 和`Static`</span><span class="sxs-lookup"><span data-stu-id="ec37e-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>

  - <span data-ttu-id="ec37e-123">參數或類型參數名稱</span><span class="sxs-lookup"><span data-stu-id="ec37e-123">Parameter or type parameter names</span></span>

  - <span data-ttu-id="ec37e-124">類型參數條件約束（適用于泛型程式）</span><span class="sxs-lookup"><span data-stu-id="ec37e-124">Type parameter constraints (for a generic procedure)</span></span>

  - <span data-ttu-id="ec37e-125">參數修飾詞關鍵字，例如 `ByRef` 和`Optional`</span><span class="sxs-lookup"><span data-stu-id="ec37e-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>

  - <span data-ttu-id="ec37e-126">是否傳回值</span><span class="sxs-lookup"><span data-stu-id="ec37e-126">Whether it returns a value</span></span>

  - <span data-ttu-id="ec37e-127">傳回值的資料類型（轉換運算子除外）</span><span class="sxs-lookup"><span data-stu-id="ec37e-127">The data type of the return value (except for a conversion operator)</span></span>

  <span data-ttu-id="ec37e-128">上述清單中的專案不是簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="ec37e-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="ec37e-129">雖然您無法使用它們來區別多載的版本，但您可以在多載的版本中，根據其簽章適當地區分它們。</span><span class="sxs-lookup"><span data-stu-id="ec37e-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>

- <span data-ttu-id="ec37e-130">**晚期繫結引數**。</span><span class="sxs-lookup"><span data-stu-id="ec37e-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="ec37e-131">如果您想要將晚期繫結的物件變數傳遞至多載版本，您必須將適當的參數宣告為 <xref:System.Object> 。</span><span class="sxs-lookup"><span data-stu-id="ec37e-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>

## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="ec37e-132">程式的多個版本</span><span class="sxs-lookup"><span data-stu-id="ec37e-132">Multiple Versions of a Procedure</span></span>

<span data-ttu-id="ec37e-133">假設您正在撰寫一個程式 `Sub` ，以根據客戶的餘額來張貼交易，而且您希望能夠依名稱或帳戶號碼來參考客戶。</span><span class="sxs-lookup"><span data-stu-id="ec37e-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="ec37e-134">為了配合此，您可以定義兩個不同 `Sub` 的程式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ec37e-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>

[!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]

### <a name="overloaded-versions"></a><span data-ttu-id="ec37e-135">多載版本</span><span class="sxs-lookup"><span data-stu-id="ec37e-135">Overloaded Versions</span></span>

<span data-ttu-id="ec37e-136">另一個方法是多載單一程式名稱。</span><span class="sxs-lookup"><span data-stu-id="ec37e-136">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="ec37e-137">您可以使用[Overloads](../../../language-reference/modifiers/overloads.md)關鍵字，為每個參數清單定義程式的版本，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ec37e-137">You can use the [Overloads](../../../language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>

[!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]

#### <a name="additional-overloads"></a><span data-ttu-id="ec37e-138">其他多載</span><span class="sxs-lookup"><span data-stu-id="ec37e-138">Additional Overloads</span></span>

<span data-ttu-id="ec37e-139">如果您也想要接受或中的交易金額 `Decimal` `Single` ，您可以進一步多載 `post` 以允許這種變化。</span><span class="sxs-lookup"><span data-stu-id="ec37e-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="ec37e-140">如果您對上述範例中的每個多載執行此操作，則會有四個 `Sub` 程式，全都具有相同的名稱，但具有四個不同的簽章。</span><span class="sxs-lookup"><span data-stu-id="ec37e-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>

## <a name="advantages-of-overloading"></a><span data-ttu-id="ec37e-141">多載的優點</span><span class="sxs-lookup"><span data-stu-id="ec37e-141">Advantages of Overloading</span></span>

<span data-ttu-id="ec37e-142">多載程式的優點是呼叫的彈性。</span><span class="sxs-lookup"><span data-stu-id="ec37e-142">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="ec37e-143">若要使用 `post` 上述範例中所宣告的程式，呼叫程式碼可以取得客戶識別做為 `String` 或 `Integer` ，然後在任一情況下呼叫相同的程式。</span><span class="sxs-lookup"><span data-stu-id="ec37e-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="ec37e-144">下列範例會加以說明：</span><span class="sxs-lookup"><span data-stu-id="ec37e-144">The following example illustrates this:</span></span>

[!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]

[!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]

## <a name="see-also"></a><span data-ttu-id="ec37e-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec37e-145">See also</span></span>

- [<span data-ttu-id="ec37e-146">程序</span><span class="sxs-lookup"><span data-stu-id="ec37e-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="ec37e-147">如何：定義程序的多個版本</span><span class="sxs-lookup"><span data-stu-id="ec37e-147">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="ec37e-148">如何：呼叫多載程序</span><span class="sxs-lookup"><span data-stu-id="ec37e-148">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="ec37e-149">如何：使用選擇性參數的多載程序</span><span class="sxs-lookup"><span data-stu-id="ec37e-149">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="ec37e-150">如何：多載使用不確定參數數目的程序</span><span class="sxs-lookup"><span data-stu-id="ec37e-150">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="ec37e-151">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="ec37e-151">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="ec37e-152">多載解析</span><span class="sxs-lookup"><span data-stu-id="ec37e-152">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="ec37e-153">多載</span><span class="sxs-lookup"><span data-stu-id="ec37e-153">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="ec37e-154">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ec37e-154">Generic Types in Visual Basic</span></span>](../data-types/generic-types.md)

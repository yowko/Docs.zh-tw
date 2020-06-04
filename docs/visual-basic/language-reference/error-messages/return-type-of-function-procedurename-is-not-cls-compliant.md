---
title: 函式 '<procedurename>' 的傳回類型不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: 9cc7e25ef1be21ff2f6a71dcb61bc29ec92da30f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400353"
---
# <a name="return-type-of-function-procedurename-is-not-cls-compliant"></a><span data-ttu-id="04012-102">函式 '\<procedurename>' 的傳回類型不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="04012-102">Return type of function '\<procedurename>' is not CLS-compliant</span></span>
<span data-ttu-id="04012-103">程式 `Function` 會標記為 `<CLSCompliant(True)>` ，但會傳回標記為、未標記或不合格的類型， `<CLSCompliant(False)>` 因為它是不相容的類型。</span><span class="sxs-lookup"><span data-stu-id="04012-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="04012-104">程序必須只使用符合 CLS 標準的型別，才能夠符合[語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md) (CLS) 標準。</span><span class="sxs-lookup"><span data-stu-id="04012-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="04012-105">這適用於參數型別、傳回型別及其所有區域變數的型別。</span><span class="sxs-lookup"><span data-stu-id="04012-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="04012-106">下列 Visual Basic 資料類型不符合 CLS 標準：</span><span class="sxs-lookup"><span data-stu-id="04012-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="04012-107">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="04012-107">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="04012-108">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="04012-108">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="04012-109">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="04012-109">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="04012-110">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="04012-110">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="04012-111">將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。</span><span class="sxs-lookup"><span data-stu-id="04012-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="04012-112">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="04012-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="04012-113">如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="04012-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="04012-114">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="04012-114">By default, this message is a warning.</span></span> <span data-ttu-id="04012-115">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="04012-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="04012-116">**錯誤識別碼：** BC40027</span><span class="sxs-lookup"><span data-stu-id="04012-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="04012-117">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="04012-117">To correct this error</span></span>  
  
- <span data-ttu-id="04012-118">如果程式 `Function` 必須傳回此特定類型，請移除 <xref:System.CLSCompliantAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="04012-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="04012-119">程序不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="04012-119">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="04012-120">如果程式 `Function` 必須符合 cls 標準，請將傳回型別變更為最符合 cls 標準的型別。</span><span class="sxs-lookup"><span data-stu-id="04012-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="04012-121">例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="04012-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="04012-122">如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="04012-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="04012-123">如果您要與 Automation 或 COM 物件互動，請記住有些類型的資料寬度與 .NET Framework 中的不同。</span><span class="sxs-lookup"><span data-stu-id="04012-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="04012-124">例如，`int` 在其他環境中通常是 16 位元。</span><span class="sxs-lookup"><span data-stu-id="04012-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="04012-125">如果您要將16位整數傳回給這類元件，請 `Short` `Integer` 在 managed Visual Basic 程式碼中將它宣告為而不是。</span><span class="sxs-lookup"><span data-stu-id="04012-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>

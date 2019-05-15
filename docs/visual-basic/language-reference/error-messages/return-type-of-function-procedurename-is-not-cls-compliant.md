---
title: 函式 '<procedurename>' 的傳回類型不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: 8d6ac07b653a27a7c4c5534f441b9d673592124c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592254"
---
# <a name="return-type-of-function-procedurename-is-not-cls-compliant"></a><span data-ttu-id="e1fbd-102">函式的傳回型別 '\<程序名稱 >' 不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="e1fbd-102">Return type of function '\<procedurename>' is not CLS-compliant</span></span>
<span data-ttu-id="e1fbd-103">A`Function`程序標示為`<CLSCompliant(True)>`但傳回類型標記為`<CLSCompliant(False)>`、 未標示，或因為它不符合規範的型別不符合資格。</span><span class="sxs-lookup"><span data-stu-id="e1fbd-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="e1fbd-104">程序必須只使用符合 CLS 規範的型別，才能夠符合[語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md) (CLS) 標準。</span><span class="sxs-lookup"><span data-stu-id="e1fbd-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="e1fbd-105">這適用於參數型別、傳回型別及其所有區域變數的型別。</span><span class="sxs-lookup"><span data-stu-id="e1fbd-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="e1fbd-106">下列 Visual Basic 資料類型不符合 CLS 標準：</span><span class="sxs-lookup"><span data-stu-id="e1fbd-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="e1fbd-107">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="e1fbd-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="e1fbd-108">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="e1fbd-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="e1fbd-109">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="e1fbd-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="e1fbd-110">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="e1fbd-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="e1fbd-111">將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。</span><span class="sxs-lookup"><span data-stu-id="e1fbd-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="e1fbd-112">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="e1fbd-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="e1fbd-113">如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="e1fbd-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="e1fbd-114">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="e1fbd-114">By default, this message is a warning.</span></span> <span data-ttu-id="e1fbd-115">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="e1fbd-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="e1fbd-116">**錯誤 ID:** BC40027</span><span class="sxs-lookup"><span data-stu-id="e1fbd-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e1fbd-117">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e1fbd-117">To correct this error</span></span>  
  
- <span data-ttu-id="e1fbd-118">如果`Function`程序必須傳回此特定的型別、 移除<xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="e1fbd-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="e1fbd-119">程序不符合 CLS 規範。</span><span class="sxs-lookup"><span data-stu-id="e1fbd-119">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="e1fbd-120">如果`Function`程序必須是符合 CLS 規範，將傳回的型別變更為最符合 CLS 規範的型別。</span><span class="sxs-lookup"><span data-stu-id="e1fbd-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="e1fbd-121">例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="e1fbd-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="e1fbd-122">如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="e1fbd-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="e1fbd-123">如果您要使用的 Automation 或 COM 物件，請記住，某些類型會有不同的資料寬度比在.NET Framework。</span><span class="sxs-lookup"><span data-stu-id="e1fbd-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="e1fbd-124">例如，`int` 在其他環境中通常是 16 位元。</span><span class="sxs-lookup"><span data-stu-id="e1fbd-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="e1fbd-125">如果傳回的這類元件的 16 位元整數，將它宣告為`Short`而不是`Integer`中受管理的 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e1fbd-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>

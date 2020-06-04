---
title: 參數 '<parametername>' 的類型不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
ms.openlocfilehash: edbcadf271c4ccafc11e5b64eb103a0290976179
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413010"
---
# <a name="type-of-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="480d0-102">參數 '\<parametername>' 的類型不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="480d0-102">Type of parameter '\<parametername>' is not CLS-compliant</span></span>
<span data-ttu-id="480d0-103">程式已標記為 `<CLSCompliant(True)>` ，但宣告的參數具有標記為、未標記或不合格的類型， `<CLSCompliant(False)>` 因為它是不相容的類型。</span><span class="sxs-lookup"><span data-stu-id="480d0-103">A procedure is marked as `<CLSCompliant(True)>` but declares a parameter with a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="480d0-104">程序必須只使用符合 CLS 標準的型別，才能夠符合[語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md) (CLS) 標準。</span><span class="sxs-lookup"><span data-stu-id="480d0-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="480d0-105">這適用於參數型別、傳回型別及其所有區域變數的型別。</span><span class="sxs-lookup"><span data-stu-id="480d0-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="480d0-106">下列 Visual Basic 資料類型不符合 CLS 標準：</span><span class="sxs-lookup"><span data-stu-id="480d0-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="480d0-107">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="480d0-107">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="480d0-108">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="480d0-108">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="480d0-109">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="480d0-109">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="480d0-110">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="480d0-110">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="480d0-111">將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。</span><span class="sxs-lookup"><span data-stu-id="480d0-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="480d0-112">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="480d0-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="480d0-113">如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="480d0-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="480d0-114">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="480d0-114">By default, this message is a warning.</span></span> <span data-ttu-id="480d0-115">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="480d0-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="480d0-116">**錯誤識別碼：** BC40028</span><span class="sxs-lookup"><span data-stu-id="480d0-116">**Error ID:** BC40028</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="480d0-117">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="480d0-117">To correct this error</span></span>  
  
- <span data-ttu-id="480d0-118">如果程式必須採用此特定類型的參數，請移除 <xref:System.CLSCompliantAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="480d0-118">If the procedure must take a parameter of this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="480d0-119">程序不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="480d0-119">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="480d0-120">如果程式必須符合 CLS 標準，請將此參數的類型變更為最符合 CLS 標準的類型。</span><span class="sxs-lookup"><span data-stu-id="480d0-120">If the procedure must be CLS-compliant, change the type of this parameter to the closest CLS-compliant type.</span></span> <span data-ttu-id="480d0-121">例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="480d0-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="480d0-122">如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="480d0-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="480d0-123">如果您要與 Automation 或 COM 物件互動，請記住有些類型的資料寬度與 .NET Framework 中的不同。</span><span class="sxs-lookup"><span data-stu-id="480d0-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="480d0-124">例如，`int` 在其他環境中通常是 16 位元。</span><span class="sxs-lookup"><span data-stu-id="480d0-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="480d0-125">如果您接受來自這類元件的16位整數，請 `Short` `Integer` 在您的 managed Visual Basic 程式碼中將它宣告為而不是。</span><span class="sxs-lookup"><span data-stu-id="480d0-125">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>

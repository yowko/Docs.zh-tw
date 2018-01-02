---
title: "選擇性的值的選擇性參數的型別&lt;parametername&gt;不符合 CLS 標準"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords: BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50ea7ce108796d099272c4a909f2fc6c81e9c77c
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="type-of-optional-value-for-optional-parameter-ltparameternamegt-is-not-cls-compliant"></a><span data-ttu-id="a25b7-102">選擇性的值的選擇性參數的型別&lt;parametername&gt;不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="a25b7-102">Type of optional value for optional parameter &lt;parametername&gt; is not CLS-compliant</span></span>
<span data-ttu-id="a25b7-103">程序已標記為 `<CLSCompliant(True)>`，但所宣告的 [Optional](../../../visual-basic/language-reference/modifiers/optional.md) 參數卻具有不符合標準之型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="a25b7-103">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../../../visual-basic/language-reference/modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>  
  
 <span data-ttu-id="a25b7-104">程序必須只使用符合 CLS 標準的型別，才能夠符合[語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md) (CLS) 標準。</span><span class="sxs-lookup"><span data-stu-id="a25b7-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="a25b7-105">這適用於參數型別、傳回型別及其所有區域變數的型別。</span><span class="sxs-lookup"><span data-stu-id="a25b7-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="a25b7-106">它也適用於選擇性參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="a25b7-106">It also applies to the default values of optional parameters.</span></span>  
  
 <span data-ttu-id="a25b7-107">下列 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 資料類型不符合 CLS 標準：</span><span class="sxs-lookup"><span data-stu-id="a25b7-107">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="a25b7-108">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="a25b7-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="a25b7-109">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="a25b7-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="a25b7-110">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="a25b7-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="a25b7-111">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="a25b7-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="a25b7-112">將 <xref:System.CLSCompliantAttribute> 屬性套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。</span><span class="sxs-lookup"><span data-stu-id="a25b7-112">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="a25b7-113">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="a25b7-113">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="a25b7-114">如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="a25b7-114">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="a25b7-115">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="a25b7-115">By default, this message is a warning.</span></span> <span data-ttu-id="a25b7-116">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="a25b7-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="a25b7-117">**錯誤識別碼：**BC40042</span><span class="sxs-lookup"><span data-stu-id="a25b7-117">**Error ID:** BC40042</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a25b7-118">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a25b7-118">To correct this error</span></span>  
  
-   <span data-ttu-id="a25b7-119">如果選擇性參數必須有這個特定類型的預設值，移除<xref:System.CLSCompliantAttribute>。</span><span class="sxs-lookup"><span data-stu-id="a25b7-119">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="a25b7-120">程序不符合 CLS 規範。</span><span class="sxs-lookup"><span data-stu-id="a25b7-120">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="a25b7-121">如果程序必須符合 CLS 標準，請將這個預設值的型別變更為最符合 CLS 標準的型別。</span><span class="sxs-lookup"><span data-stu-id="a25b7-121">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="a25b7-122">例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="a25b7-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="a25b7-123">如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="a25b7-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="a25b7-124">如果您要與 Automation 或 COM 物件進行互動，請記住，某些型別的資料寬度會與在 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 中的資料寬度不同。</span><span class="sxs-lookup"><span data-stu-id="a25b7-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="a25b7-125">例如，`int` 在其他環境中通常是 16 位元。</span><span class="sxs-lookup"><span data-stu-id="a25b7-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="a25b7-126">如果您所接收的是來自這類元件的 16 位元整數，請在您的 Managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 程式碼中將它宣告為 `Short` 而不是 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="a25b7-126">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>
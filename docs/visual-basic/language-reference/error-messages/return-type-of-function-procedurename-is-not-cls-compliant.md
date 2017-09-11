---
title: "函式的傳回型別 &quot;&lt;m e&gt;&quot; 不符合 CLS 標準 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40027
- vbc40027
dev_langs:
- VB
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 949104d77996cb7678bb9841cd1cd1e9b7f71b56
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="return-type-of-function-39ltprocedurenamegt39-is-not-cls-compliant"></a><span data-ttu-id="2859d-102">函式的傳回型別 '&lt;m e&gt;' 不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="2859d-102">Return type of function &#39;&lt;procedurename&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="2859d-103">A`Function`程序會標示為`<CLSCompliant(True)>`，但會傳回型別標示為`<CLSCompliant(False)>`、 未標記，或因為它是不相容的類型不符合。</span><span class="sxs-lookup"><span data-stu-id="2859d-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="2859d-104">程序必須只使用符合 CLS 規範的型別，才能夠符合[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3) (CLS) 標準。</span><span class="sxs-lookup"><span data-stu-id="2859d-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="2859d-105">這適用於參數型別、傳回型別及其所有區域變數的型別。</span><span class="sxs-lookup"><span data-stu-id="2859d-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="2859d-106">下列 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 資料類型不符合 CLS 規範：</span><span class="sxs-lookup"><span data-stu-id="2859d-106">The following [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="2859d-107">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="2859d-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="2859d-108">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="2859d-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="2859d-109">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="2859d-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="2859d-110">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="2859d-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="2859d-111">當您將套用<xref:System.CLSCompliantAttribute>程式設計項目，您可以設定屬性的`isCompliant`參數為`True`或`False`表示相容或不相容。</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="2859d-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="2859d-112">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="2859d-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="2859d-113">如果您不會套用<xref:System.CLSCompliantAttribute>的項目，它會被視為不相容。</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="2859d-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="2859d-114">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="2859d-114">By default, this message is a warning.</span></span> <span data-ttu-id="2859d-115">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="2859d-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="2859d-116">**錯誤識別碼︰** BC40027</span><span class="sxs-lookup"><span data-stu-id="2859d-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2859d-117">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="2859d-117">To correct this error</span></span>  
  
-   <span data-ttu-id="2859d-118">如果`Function`程序必須傳回此特定的型別、 移除<xref:System.CLSCompliantAttribute>.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="2859d-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="2859d-119">程序不符合 CLS 規範。</span><span class="sxs-lookup"><span data-stu-id="2859d-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="2859d-120">如果`Function`程序必須是符合 CLS 標準，將傳回的型別變更為最符合 CLS 標準的型別。</span><span class="sxs-lookup"><span data-stu-id="2859d-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="2859d-121">例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="2859d-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="2859d-122">如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="2859d-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="2859d-123">如果您要與 Automation 或 COM 物件進行互動，請記住，某些型別的資料寬度會與在 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 中的資料寬度不同。</span><span class="sxs-lookup"><span data-stu-id="2859d-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span> <span data-ttu-id="2859d-124">例如，`int` 在其他環境中通常是 16 位元。</span><span class="sxs-lookup"><span data-stu-id="2859d-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="2859d-125">如果傳回 16 位元整數的這類元件，將它宣告為`Short`而不是`Integer`中 managed[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式碼。</span><span class="sxs-lookup"><span data-stu-id="2859d-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2859d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2859d-126">See Also</span></span>  
 [<span data-ttu-id="2859d-127">\<PAVE OVER > 撰寫符合 CLS 標準的程式碼</span><span class="sxs-lookup"><span data-stu-id="2859d-127">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)

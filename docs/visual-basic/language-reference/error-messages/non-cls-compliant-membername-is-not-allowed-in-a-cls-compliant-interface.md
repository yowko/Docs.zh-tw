---
title: 符合 CLS 標準的介面中不允許有不符合 CLS 標準的 <membername>
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: e572189b958612bf9527c82ce702df3ab929a23f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409396"
---
# <a name="non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="e86eb-102">符合 CLS 標準的介面中不允許有不符合 CLS 標準的 \<membername></span><span class="sxs-lookup"><span data-stu-id="e86eb-102">Non-CLS-compliant \<membername> is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="e86eb-103">介面中的屬性、程式或事件會標記為 `<CLSCompliant(True)>` 介面本身標記為 `<CLSCompliant(False)>` 或未標記時。</span><span class="sxs-lookup"><span data-stu-id="e86eb-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="e86eb-104">若要讓介面符合[語言獨立性和與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（CLS），其所有成員都必須符合規範。</span><span class="sxs-lookup"><span data-stu-id="e86eb-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="e86eb-105">將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。</span><span class="sxs-lookup"><span data-stu-id="e86eb-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="e86eb-106">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="e86eb-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="e86eb-107">如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="e86eb-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="e86eb-108">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="e86eb-108">By default, this message is a warning.</span></span> <span data-ttu-id="e86eb-109">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="e86eb-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="e86eb-110">**錯誤識別碼：** BC40033</span><span class="sxs-lookup"><span data-stu-id="e86eb-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e86eb-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e86eb-111">To correct this error</span></span>  
  
- <span data-ttu-id="e86eb-112">如果您需要 CLS 符合性，而且可以控制介面原始程式碼，請將介面標示為 `<CLSCompliant(True)>` 符合其所有成員的規範。</span><span class="sxs-lookup"><span data-stu-id="e86eb-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
- <span data-ttu-id="e86eb-113">如果您需要 CLS 合規性，而且無法控制介面原始程式碼，或如果不符合規範，請在不同的介面中定義這個成員。</span><span class="sxs-lookup"><span data-stu-id="e86eb-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
- <span data-ttu-id="e86eb-114">如果您要求這個成員保留在其目前的介面中，請 <xref:System.CLSCompliantAttribute> 從其定義中移除，或將其標記為 `<CLSCompliant(False)>` 。</span><span class="sxs-lookup"><span data-stu-id="e86eb-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e86eb-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e86eb-115">See also</span></span>

- [<span data-ttu-id="e86eb-116">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="e86eb-116">Interface Statement</span></span>](../statements/interface-statement.md)

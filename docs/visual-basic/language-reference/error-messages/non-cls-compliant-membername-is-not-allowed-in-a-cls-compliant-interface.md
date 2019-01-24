---
title: 非 CLS 相容&lt;membername&gt;符合 CLS 規範的介面中不允許
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: c837065d2d448fc2523cfbd18efac962445f8bf0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627690"
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="b0345-102">非 CLS 相容&lt;membername&gt;符合 CLS 規範的介面中不允許</span><span class="sxs-lookup"><span data-stu-id="b0345-102">Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="b0345-103">屬性、 程序或在介面中的事件標示為`<CLSCompliant(True)>`介面本身會標示為`<CLSCompliant(False)>`或未標記。</span><span class="sxs-lookup"><span data-stu-id="b0345-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="b0345-104">若要符合介面[Language Independence and Language-independent Components](../../../standard/language-independence-and-language-independent-components.md) （cls） 標準，其所有成員必須都是符合規範。</span><span class="sxs-lookup"><span data-stu-id="b0345-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="b0345-105">將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。</span><span class="sxs-lookup"><span data-stu-id="b0345-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="b0345-106">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="b0345-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="b0345-107">如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="b0345-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="b0345-108">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="b0345-108">By default, this message is a warning.</span></span> <span data-ttu-id="b0345-109">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="b0345-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b0345-110">**錯誤 ID:** BC40033</span><span class="sxs-lookup"><span data-stu-id="b0345-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b0345-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b0345-111">To correct this error</span></span>  
  
-   <span data-ttu-id="b0345-112">如果您需要 cls 符合性，而且可以控制介面的原始碼，將標示為介面`<CLSCompliant(True)>`其所有成員是否符合規範。</span><span class="sxs-lookup"><span data-stu-id="b0345-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
-   <span data-ttu-id="b0345-113">如果您需要 cls 符合性，而且不需要控制介面的原始碼，或它不會不符合 cls 標準，定義這個成員在不同的介面。</span><span class="sxs-lookup"><span data-stu-id="b0345-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
-   <span data-ttu-id="b0345-114">如果您想要將這個成員保留其目前的介面中，移除<xref:System.CLSCompliantAttribute>從其定義或將其標記為`<CLSCompliant(False)>`。</span><span class="sxs-lookup"><span data-stu-id="b0345-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0345-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0345-115">See also</span></span>
- [<span data-ttu-id="b0345-116">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="b0345-116">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)


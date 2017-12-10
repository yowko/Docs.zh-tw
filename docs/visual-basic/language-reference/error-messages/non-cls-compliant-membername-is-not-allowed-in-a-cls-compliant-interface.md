---
title: "非 CLS 相容&lt;membername&gt;符合 CLS 標準的介面中不允許"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords: BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2811958df5bd0b023a2ce3b02abf85b5a23c58f6
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2017
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="af597-102">非 CLS 相容&lt;membername&gt;符合 CLS 標準的介面中不允許</span><span class="sxs-lookup"><span data-stu-id="af597-102">Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="af597-103">屬性、 程序或在介面中的事件標記為`<CLSCompliant(True)>`當介面本身標示為`<CLSCompliant(False)>`或未標記。</span><span class="sxs-lookup"><span data-stu-id="af597-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="af597-104">若要符合介面[語言獨立性以及與語言無關的元件](../../../../docs/standard/language-independence-and-language-independent-components.md)（cls） 標準，其所有成員都必須相容。</span><span class="sxs-lookup"><span data-stu-id="af597-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="af597-105">將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。</span><span class="sxs-lookup"><span data-stu-id="af597-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="af597-106">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="af597-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="af597-107">如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="af597-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="af597-108">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="af597-108">By default, this message is a warning.</span></span> <span data-ttu-id="af597-109">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="af597-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="af597-110">**錯誤 ID:** BC40033</span><span class="sxs-lookup"><span data-stu-id="af597-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="af597-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="af597-111">To correct this error</span></span>  
  
-   <span data-ttu-id="af597-112">如果您需要 cls 符合性，而且能夠控制介面原始程式碼，標記為介面`<CLSCompliant(True)>`如果其所有成員都均相容。</span><span class="sxs-lookup"><span data-stu-id="af597-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
-   <span data-ttu-id="af597-113">如果您需要 cls 符合性，而且不需要控制介面的原始碼，或是它不符合標準，定義這個成員在不同的介面。</span><span class="sxs-lookup"><span data-stu-id="af597-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
-   <span data-ttu-id="af597-114">如果您想要將這個成員保留其目前的介面中，移除<xref:System.CLSCompliantAttribute>從其定義或將其標記為`<CLSCompliant(False)>`。</span><span class="sxs-lookup"><span data-stu-id="af597-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af597-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af597-115">See Also</span></span>  
 [<span data-ttu-id="af597-116">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="af597-116">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="af597-117">\<PAVE OVER > 撰寫符合 CLS 標準的程式碼</span><span class="sxs-lookup"><span data-stu-id="af597-117">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)

---
title: "非 CLS 相容&lt;membername&gt;符合 CLS 標準的介面中不允許 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40033
- vbc40033
dev_langs:
- VB
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: 9
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
ms.openlocfilehash: 27e83344c68d73c992d2395ab5d1bfcdb67520b0
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="df059-102">非 CLS 相容&lt;membername&gt;符合 CLS 標準的介面中不允許</span><span class="sxs-lookup"><span data-stu-id="df059-102">Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="df059-103">屬性、 程序或事件的介面中標示為`<CLSCompliant(True)>`介面本身會標示為`<CLSCompliant(False)>`或未標記。</span><span class="sxs-lookup"><span data-stu-id="df059-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="df059-104">為了符合介面[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3)(CLS)，其所有成員都必須相容。</span><span class="sxs-lookup"><span data-stu-id="df059-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="df059-105">當您將套用<xref:System.CLSCompliantAttribute>程式設計項目，您可以設定屬性的`isCompliant`參數為`True`或`False`表示相容或不相容。</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="df059-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="df059-106">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="df059-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="df059-107">如果您不會套用<xref:System.CLSCompliantAttribute>的項目，它會被視為不相容。</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="df059-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="df059-108">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="df059-108">By default, this message is a warning.</span></span> <span data-ttu-id="df059-109">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="df059-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="df059-110">**錯誤識別碼︰** BC40033</span><span class="sxs-lookup"><span data-stu-id="df059-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="df059-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="df059-111">To correct this error</span></span>  
  
-   <span data-ttu-id="df059-112">如果您需要將 cls 符合性，而且介面原始程式碼控制，將介面標記為`<CLSCompliant(True)>`如果其所有成員都都相容。</span><span class="sxs-lookup"><span data-stu-id="df059-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
-   <span data-ttu-id="df059-113">如果需要將 cls 符合性，而且不需要控制介面的原始碼，或它不會不符合 cls 標準，定義此成員內不同的介面。</span><span class="sxs-lookup"><span data-stu-id="df059-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
-   <span data-ttu-id="df059-114">如果您需要這個成員會維持其目前的介面中，移除<xref:System.CLSCompliantAttribute>從其定義或標示為`<CLSCompliant(False)>`。</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="df059-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df059-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df059-115">See Also</span></span>  
 <span data-ttu-id="df059-116">[Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md) </span><span class="sxs-lookup"><span data-stu-id="df059-116">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) </span></span>  
<span data-ttu-id="df059-117"> [\<PAVE OVER > 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span><span class="sxs-lookup"><span data-stu-id="df059-117"> [\<PAVE OVER> Writing CLS-Compliant Code](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span></span>

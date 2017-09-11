---
title: "&quot;&lt;classname&gt;&quot; 不符合 CLS 標準，因為介面 &quot;&lt;interfacename&gt;&quot; 它會實作不符合 CLS 標準 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
dev_langs:
- VB
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
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
ms.openlocfilehash: d2819bf2dc76291cbaf7ca9215608a11b1a98b3a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a><span data-ttu-id="7a9d6-102">'&lt;classname&gt;' 不符合 CLS 標準，因為介面 '&lt;interfacename&gt;' 它會實作不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="7a9d6-102">&#39;&lt;classname&gt;&#39; is not CLS-compliant because the interface &#39;&lt;interfacename&gt;&#39; it implements is not CLS-compliant</span></span>
<span data-ttu-id="7a9d6-103">當類別或介面衍生自或實作標記為 `<CLSCompliant(True)>` 或未標記的類型時，則標記為 `<CLSCompliant(False)>` 。</span><span class="sxs-lookup"><span data-stu-id="7a9d6-103">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="7a9d6-104">類別或介面，以符合[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3)(CLS)，其整個繼承階層架構必須相容。</span><span class="sxs-lookup"><span data-stu-id="7a9d6-104">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="7a9d6-105">這表示它直接或間接繼承的每個類型都必須符合規範。</span><span class="sxs-lookup"><span data-stu-id="7a9d6-105">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="7a9d6-106">同樣地，如果類別實作一或多個介面，則它們在整個繼承階層都必須符合規範。</span><span class="sxs-lookup"><span data-stu-id="7a9d6-106">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>  
  
 <span data-ttu-id="7a9d6-107">當您將套用<xref:System.CLSCompliantAttribute>程式設計項目，您可以設定屬性的`isCompliant`參數為`True`或`False`表示相容或不相容。</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="7a9d6-107">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="7a9d6-108">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="7a9d6-108">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="7a9d6-109">如果您不會套用<xref:System.CLSCompliantAttribute>的項目，它會被視為不相容。</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="7a9d6-109">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="7a9d6-110">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="7a9d6-110">By default, this message is a warning.</span></span> <span data-ttu-id="7a9d6-111">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="7a9d6-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="7a9d6-112">**錯誤識別碼︰** BC40029</span><span class="sxs-lookup"><span data-stu-id="7a9d6-112">**Error ID:** BC40029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7a9d6-113">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="7a9d6-113">To correct this error</span></span>  
  
-   <span data-ttu-id="7a9d6-114">如果您必須符合 CLS 規範，請在不同的繼承階層或實作配置內定義這個類型。</span><span class="sxs-lookup"><span data-stu-id="7a9d6-114">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>  
  
-   <span data-ttu-id="7a9d6-115">如果您需要此類型會保留其目前的繼承階層架構或實作配置中，移除<xref:System.CLSCompliantAttribute>從其定義或標示為`<CLSCompliant(False)>`。</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="7a9d6-115">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a9d6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a9d6-116">See Also</span></span>  
 [<span data-ttu-id="7a9d6-117">\<PAVE OVER > 撰寫符合 CLS 標準的程式碼</span><span class="sxs-lookup"><span data-stu-id="7a9d6-117">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)

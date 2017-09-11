---
title: "名稱&lt;membername&gt;不符合 CLS 標準 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40031
- vbc40031
dev_langs:
- VB
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
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
ms.openlocfilehash: cbe0a8db6d801a0d083a6828af75342f15f0178d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a><span data-ttu-id="13902-102">名稱&lt;membername&gt;不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="13902-102">Name &lt;membername&gt; is not CLS-compliant</span></span>
<span data-ttu-id="13902-103">組件標示為`<CLSCompliant(True)>`但公開成員的名稱開頭為底線 (`_`)。</span><span class="sxs-lookup"><span data-stu-id="13902-103">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="13902-104">程式設計項目可以包含一或多個底線，但要遵守[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3)(CLS)，它必須未以底線開頭。</span><span class="sxs-lookup"><span data-stu-id="13902-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="13902-105">請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="13902-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="13902-106">當您將套用<xref:System.CLSCompliantAttribute>程式設計項目，您可以設定屬性的`isCompliant`參數為`True`或`False`表示相容或不相容。</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="13902-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="13902-107">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="13902-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="13902-108">如果您不會套用<xref:System.CLSCompliantAttribute>的項目，它會被視為不相容。</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="13902-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="13902-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="13902-109">By default, this message is a warning.</span></span> <span data-ttu-id="13902-110">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="13902-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="13902-111">**錯誤識別碼︰** BC40031</span><span class="sxs-lookup"><span data-stu-id="13902-111">**Error ID:** BC40031</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="13902-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="13902-112">To correct this error</span></span>  
  
-   <span data-ttu-id="13902-113">如果您有原始程式碼控制，變更成員名稱，使它不是以底線開頭。</span><span class="sxs-lookup"><span data-stu-id="13902-113">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>  
  
-   <span data-ttu-id="13902-114">如果您需要的成員名稱保持不變，移除<xref:System.CLSCompliantAttribute>從其定義或標示為`<CLSCompliant(False)>`。</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="13902-114">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="13902-115">您仍然可以將標記的組件`<CLSCompliant(True)>`。</span><span class="sxs-lookup"><span data-stu-id="13902-115">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13902-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13902-116">See Also</span></span>  
 <span data-ttu-id="13902-117">[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="13902-117">[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="13902-118"> [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="13902-118"> [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span></span>  
<span data-ttu-id="13902-119"> [\<PAVE OVER > 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span><span class="sxs-lookup"><span data-stu-id="13902-119"> [\<PAVE OVER> Writing CLS-Compliant Code](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span></span>

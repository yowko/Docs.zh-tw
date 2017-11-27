---
title: "名稱&lt;membername&gt;不符合 CLS 標準"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords: BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7f574c2ebd71dbe06c4a687728e7812a18c8a949
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a><span data-ttu-id="52723-102">名稱&lt;membername&gt;不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="52723-102">Name &lt;membername&gt; is not CLS-compliant</span></span>
<span data-ttu-id="52723-103">組件標示為`<CLSCompliant(True)>`但公開的成員名稱開頭為底線 (`_`)。</span><span class="sxs-lookup"><span data-stu-id="52723-103">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="52723-104">程式設計項目可以包含一或多個底線，但若要遵守[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3)（cls） 標準，它必須不以底線開頭。</span><span class="sxs-lookup"><span data-stu-id="52723-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="52723-105">請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="52723-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="52723-106">將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。</span><span class="sxs-lookup"><span data-stu-id="52723-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="52723-107">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="52723-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="52723-108">如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="52723-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="52723-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="52723-109">By default, this message is a warning.</span></span> <span data-ttu-id="52723-110">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="52723-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="52723-111">**錯誤 ID:** BC40031</span><span class="sxs-lookup"><span data-stu-id="52723-111">**Error ID:** BC40031</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="52723-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="52723-112">To correct this error</span></span>  
  
-   <span data-ttu-id="52723-113">如果您有原始程式碼控制，變更成員名稱，使它不是以底線開頭。</span><span class="sxs-lookup"><span data-stu-id="52723-113">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>  
  
-   <span data-ttu-id="52723-114">如果您需要的成員名稱維持不變，移除<xref:System.CLSCompliantAttribute>從其定義或將其標記為`<CLSCompliant(False)>`。</span><span class="sxs-lookup"><span data-stu-id="52723-114">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="52723-115">您仍可以標示為組件`<CLSCompliant(True)>`。</span><span class="sxs-lookup"><span data-stu-id="52723-115">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52723-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52723-116">See Also</span></span>  
 [<span data-ttu-id="52723-117">宣告項目名稱</span><span class="sxs-lookup"><span data-stu-id="52723-117">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="52723-118">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="52723-118">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="52723-119">\<PAVE OVER > 撰寫符合 CLS 標準的程式碼</span><span class="sxs-lookup"><span data-stu-id="52723-119">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)

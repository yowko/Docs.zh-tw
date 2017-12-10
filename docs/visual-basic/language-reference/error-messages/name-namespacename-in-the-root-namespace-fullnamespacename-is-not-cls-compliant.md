---
title: "名稱&lt;namespacename&gt;根命名空間中&lt;fullnamespacename&gt;不符合 CLS 標準"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords: BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 36de8b6a27c47e9e7192aed10e6b561bb0c07acc
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2017
---
# <a name="name-ltnamespacenamegt-in-the-root-namespace-ltfullnamespacenamegt-is-not-cls-compliant"></a><span data-ttu-id="17e93-102">名稱&lt;namespacename&gt;根命名空間中&lt;fullnamespacename&gt;不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="17e93-102">Name &lt;namespacename&gt; in the root namespace &lt;fullnamespacename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="17e93-103">組件標示為`<CLSCompliant(True)>`，但根命名空間名稱的項目開頭為底線 (`_`)。</span><span class="sxs-lookup"><span data-stu-id="17e93-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="17e93-104">程式設計項目可以包含一或多個底線，但若要遵守[語言獨立性以及與語言無關的元件](../../../../docs/standard/language-independence-and-language-independent-components.md)（cls） 標準，它必須不以底線開頭。</span><span class="sxs-lookup"><span data-stu-id="17e93-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="17e93-105">請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="17e93-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="17e93-106">將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。</span><span class="sxs-lookup"><span data-stu-id="17e93-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="17e93-107">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="17e93-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="17e93-108">如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="17e93-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="17e93-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="17e93-109">By default, this message is a warning.</span></span> <span data-ttu-id="17e93-110">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="17e93-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="17e93-111">**錯誤 ID:** BC40039</span><span class="sxs-lookup"><span data-stu-id="17e93-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="17e93-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="17e93-112">To correct this error</span></span>  
  
-   <span data-ttu-id="17e93-113">如果您需要 cls 符合性，請變更根命名空間名稱，使它的所有元素的開頭為底線。</span><span class="sxs-lookup"><span data-stu-id="17e93-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
-   <span data-ttu-id="17e93-114">如果您需要的命名空間名稱保持不變，則請移除<xref:System.CLSCompliantAttribute>從組件或將其標記為`<CLSCompliant(False)>`。</span><span class="sxs-lookup"><span data-stu-id="17e93-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e93-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17e93-115">See Also</span></span>  
 [<span data-ttu-id="17e93-116">Namespace 陳述式</span><span class="sxs-lookup"><span data-stu-id="17e93-116">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="17e93-117">在 Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="17e93-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="17e93-118">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="17e93-118">/rootnamespace</span></span>](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)  
 [<span data-ttu-id="17e93-119">專案設計工具、應用程式頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17e93-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [<span data-ttu-id="17e93-120">宣告項目名稱</span><span class="sxs-lookup"><span data-stu-id="17e93-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="17e93-121">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="17e93-121">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="17e93-122">\<PAVE OVER > 撰寫符合 CLS 標準的程式碼</span><span class="sxs-lookup"><span data-stu-id="17e93-122">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)

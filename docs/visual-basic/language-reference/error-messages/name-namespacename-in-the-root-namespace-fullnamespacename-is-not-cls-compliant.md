---
title: 根命名空間 <namespacename> 中的名稱 <fullnamespacename> 不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: 821044d3ee359a052fa6a763e9c5a89da5d6f607
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775574"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a><span data-ttu-id="8c5f6-102">根命名空間中的名稱 \<namespacename > \<fullnamespacename > 不符合 CLS 規範</span><span class="sxs-lookup"><span data-stu-id="8c5f6-102">Name \<namespacename> in the root namespace \<fullnamespacename> is not CLS-compliant</span></span>
<span data-ttu-id="8c5f6-103">元件標示為 `<CLSCompliant(True)>`，但根命名空間名稱的元素以底線（`_`）開頭。</span><span class="sxs-lookup"><span data-stu-id="8c5f6-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="8c5f6-104">程式設計專案可以包含一或多個底線，但若要符合[語言獨立性和與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（CLS）的規範，其開頭不得為底線。</span><span class="sxs-lookup"><span data-stu-id="8c5f6-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="8c5f6-105">請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="8c5f6-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="8c5f6-106">將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。</span><span class="sxs-lookup"><span data-stu-id="8c5f6-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="8c5f6-107">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="8c5f6-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="8c5f6-108">如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="8c5f6-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="8c5f6-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="8c5f6-109">By default, this message is a warning.</span></span> <span data-ttu-id="8c5f6-110">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="8c5f6-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="8c5f6-111">**錯誤識別碼：** BC40039</span><span class="sxs-lookup"><span data-stu-id="8c5f6-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8c5f6-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="8c5f6-112">To correct this error</span></span>  
  
- <span data-ttu-id="8c5f6-113">如果您需要 CLS 合規性，請變更根命名空間名稱，使其所有元素的開頭都是底線。</span><span class="sxs-lookup"><span data-stu-id="8c5f6-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
- <span data-ttu-id="8c5f6-114">如果您需要命名空間名稱保持不變，請從元件中移除 <xref:System.CLSCompliantAttribute>，或將其標示為 `<CLSCompliant(False)>`。</span><span class="sxs-lookup"><span data-stu-id="8c5f6-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c5f6-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="8c5f6-115">See also</span></span>

- [<span data-ttu-id="8c5f6-116">Namespace 陳述式</span><span class="sxs-lookup"><span data-stu-id="8c5f6-116">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="8c5f6-117">Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="8c5f6-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="8c5f6-118">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="8c5f6-118">-rootnamespace</span></span>](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [<span data-ttu-id="8c5f6-119">專案設計工具、應用程式頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c5f6-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="8c5f6-120">宣告項目名稱</span><span class="sxs-lookup"><span data-stu-id="8c5f6-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="8c5f6-121">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="8c5f6-121">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)

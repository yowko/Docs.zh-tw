---
title: 名稱 <membername> 不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 33b60b2212d25737330dc93d7ba2715e4d5865b7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873703"
---
# <a name="name-membername-is-not-cls-compliant"></a><span data-ttu-id="3284d-102">名稱 \<membername> 不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="3284d-102">Name \<membername> is not CLS-compliant</span></span>

<span data-ttu-id="3284d-103">元件會標示為， `<CLSCompliant(True)>` 但會使用開頭為底線 () 的名稱來公開成員 `_` 。</span><span class="sxs-lookup"><span data-stu-id="3284d-103">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="3284d-104">程式設計專案可以包含一或多個底線，但為了符合 [語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md) (cls) ，它不能以底線開頭。</span><span class="sxs-lookup"><span data-stu-id="3284d-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="3284d-105">請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="3284d-105">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="3284d-106">將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。</span><span class="sxs-lookup"><span data-stu-id="3284d-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="3284d-107">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="3284d-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="3284d-108">如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="3284d-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="3284d-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="3284d-109">By default, this message is a warning.</span></span> <span data-ttu-id="3284d-110">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="3284d-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="3284d-111">**錯誤識別碼：** BC40031</span><span class="sxs-lookup"><span data-stu-id="3284d-111">**Error ID:** BC40031</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3284d-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="3284d-112">To correct this error</span></span>  
  
- <span data-ttu-id="3284d-113">如果您有原始程式碼的控制權，請變更成員名稱，使它不是以底線開頭。</span><span class="sxs-lookup"><span data-stu-id="3284d-113">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>  
  
- <span data-ttu-id="3284d-114">如果您要求成員名稱保持不變，請 <xref:System.CLSCompliantAttribute> 從其定義中移除，或將它標示為 `<CLSCompliant(False)>` 。</span><span class="sxs-lookup"><span data-stu-id="3284d-114">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="3284d-115">您仍然可以將元件標示為 `<CLSCompliant(True)>` 。</span><span class="sxs-lookup"><span data-stu-id="3284d-115">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3284d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3284d-116">See also</span></span>

- [<span data-ttu-id="3284d-117">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="3284d-117">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="3284d-118">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="3284d-118">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)

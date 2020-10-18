---
title: 因為 <proceduresignature1> 多載了<proceduresignature2>，不同於只在於陣列參數類型的陣列，或是陣列參數類型的順位，所以不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 5376f0513b1180da511a508cf8e0e754e8938384
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159790"
---
# <a name="bc40035-proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="b14c8-102">BC40035：不符合 \<proceduresignature1> CLS 規範，因為它的多載 \<proceduresignature2> 與陣列參數類型的陣列或陣列參數類型的順位不同</span><span class="sxs-lookup"><span data-stu-id="b14c8-102">BC40035: \<proceduresignature1> is not CLS-compliant because it overloads \<proceduresignature2> which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>

<span data-ttu-id="b14c8-103">程式或屬性會標示為 `<CLSCompliant(True)>` 覆寫另一個程式或屬性，而且其參數清單之間的唯一差異是不規則陣列的嵌套層級或陣列的順位。</span><span class="sxs-lookup"><span data-stu-id="b14c8-103">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>

 <span data-ttu-id="b14c8-104">在下列宣告中，第二個和第三個宣告會產生此錯誤：</span><span class="sxs-lookup"><span data-stu-id="b14c8-104">In the following declarations, the second and third declarations generate this error:</span></span>

 `Overloads Sub ProcessArray(arrayParam() As Integer)`

 `Overloads Sub ProcessArray(arrayParam()() As Integer)`

 `Overloads Sub ProcessArray(arrayParam(,) As Integer)`

 <span data-ttu-id="b14c8-105">第二個宣告會將原始的一維參數變更 `arrayParam` 為數組的陣列。</span><span class="sxs-lookup"><span data-stu-id="b14c8-105">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="b14c8-106">第三個宣告會變更 `arrayParam` 為二維陣列， (排名 2) 。</span><span class="sxs-lookup"><span data-stu-id="b14c8-106">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="b14c8-107">雖然 Visual Basic 可讓多載只因上述其中一項變更而不同，但這種多載不符合 (CLS) 的 [語言獨立性和 Language-Independent 元件](../../../standard/language-independence-and-language-independent-components.md) 。</span><span class="sxs-lookup"><span data-stu-id="b14c8-107">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>

 <span data-ttu-id="b14c8-108">將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。</span><span class="sxs-lookup"><span data-stu-id="b14c8-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="b14c8-109">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="b14c8-109">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="b14c8-110">如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="b14c8-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="b14c8-111">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="b14c8-111">By default, this message is a warning.</span></span> <span data-ttu-id="b14c8-112">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="b14c8-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="b14c8-113">**錯誤識別碼：** BC40035</span><span class="sxs-lookup"><span data-stu-id="b14c8-113">**Error ID:** BC40035</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b14c8-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b14c8-114">To correct this error</span></span>

- <span data-ttu-id="b14c8-115">如果您需要 CLS 合規性，請將多載定義為不同于此說明頁面上所提及之變更的方式。</span><span class="sxs-lookup"><span data-stu-id="b14c8-115">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>
- <span data-ttu-id="b14c8-116">如果您要求多載的差異只在於此說明頁面上所述的變更，請 <xref:System.CLSCompliantAttribute> 從其定義中移除，或將它們標示為 `<CLSCompliant(False)>` 。</span><span class="sxs-lookup"><span data-stu-id="b14c8-116">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b14c8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b14c8-117">See also</span></span>

- [<span data-ttu-id="b14c8-118">程序多載化</span><span class="sxs-lookup"><span data-stu-id="b14c8-118">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="b14c8-119">多載</span><span class="sxs-lookup"><span data-stu-id="b14c8-119">Overloads</span></span>](../modifiers/overloads.md)

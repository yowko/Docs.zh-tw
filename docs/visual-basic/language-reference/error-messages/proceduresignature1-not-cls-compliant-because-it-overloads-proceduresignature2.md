---
title: <proceduresignature1> 不符合 CLS 標準，因為它多載<proceduresignature2>的差別只在於陣列參數類型的陣列，或是陣列參數類型的陣序規範
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 0bda4ad6a4d5368d93e2ca603b78bf9db6aca858
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920909"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="6e08c-102">\<proceduresignature1 > 不符合 CLS 標準，因為它多載\<proceduresignature2 > 的差別只在於陣列參數類型的陣列，或是陣列參數類型的陣序規範</span><span class="sxs-lookup"><span data-stu-id="6e08c-102">\<proceduresignature1> is not CLS-compliant because it overloads \<proceduresignature2> which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>
<span data-ttu-id="6e08c-103">程序或屬性會標示為`<CLSCompliant(True)>`時它會覆寫另一個程序或屬性和其參數清單之間唯一的差別是巢狀層級的不規則陣列陣序。</span><span class="sxs-lookup"><span data-stu-id="6e08c-103">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>  
  
 <span data-ttu-id="6e08c-104">在下列宣告中，第二個和第三個宣告會產生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="6e08c-104">In the following declarations, the second and third declarations generate this error.</span></span>  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 <span data-ttu-id="6e08c-105">第二個宣告會變更原始的一維參數`arrayParam`至陣列的陣列。</span><span class="sxs-lookup"><span data-stu-id="6e08c-105">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="6e08c-106">第三個宣告的變更`arrayParam`二維陣列 （也就是陣序 2）。</span><span class="sxs-lookup"><span data-stu-id="6e08c-106">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="6e08c-107">Visual Basic 可讓不同僅由其中一個這些變更的多載，這類多載與不相容[Language Independence and Language-independent Components](../../../standard/language-independence-and-language-independent-components.md) （cls） 標準。</span><span class="sxs-lookup"><span data-stu-id="6e08c-107">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="6e08c-108">將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。</span><span class="sxs-lookup"><span data-stu-id="6e08c-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="6e08c-109">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="6e08c-109">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="6e08c-110">如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="6e08c-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="6e08c-111">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="6e08c-111">By default, this message is a warning.</span></span> <span data-ttu-id="6e08c-112">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="6e08c-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="6e08c-113">**錯誤 ID:** BC40035</span><span class="sxs-lookup"><span data-stu-id="6e08c-113">**Error ID:** BC40035</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6e08c-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="6e08c-114">To correct this error</span></span>  
  
- <span data-ttu-id="6e08c-115">如果您需要 cls 符合性，定義您的多載方面與彼此不同，在更多的方法，只將這個說明網頁所述的變更。</span><span class="sxs-lookup"><span data-stu-id="6e08c-115">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>  
  
- <span data-ttu-id="6e08c-116">如果您需要多載的差別只能由引用此說明的變更頁面上，移除<xref:System.CLSCompliantAttribute>從其定義或將它們標記為`<CLSCompliant(False)>`。</span><span class="sxs-lookup"><span data-stu-id="6e08c-116">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e08c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e08c-117">See also</span></span>

- [<span data-ttu-id="6e08c-118">程序多載化</span><span class="sxs-lookup"><span data-stu-id="6e08c-118">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="6e08c-119">多載</span><span class="sxs-lookup"><span data-stu-id="6e08c-119">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)

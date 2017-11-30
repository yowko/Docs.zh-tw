---
title: "&lt;proceduresignature1&gt;不符合 CLS 標準，因為它多載&lt;proceduresignature2&gt;的差別只在於陣列參數類型的陣列，或是陣列參數類型的陣序規範"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords: BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fa9fca7f0590846f60577787aa476539a2c872a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="60808-102">&lt;proceduresignature1&gt;不符合 CLS 標準，因為它多載&lt;proceduresignature2&gt;的差別只在於陣列參數類型的陣列，或是陣列參數類型的陣序規範</span><span class="sxs-lookup"><span data-stu-id="60808-102">&lt;proceduresignature1&gt; is not CLS-compliant because it overloads &lt;proceduresignature2&gt; which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>
<span data-ttu-id="60808-103">程序或屬性標示為`<CLSCompliant(True)>`時它會覆寫另一個程序或屬性和其參數清單中唯一的差別是巢狀的層級的不規則陣列陣序。</span><span class="sxs-lookup"><span data-stu-id="60808-103">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>  
  
 <span data-ttu-id="60808-104">在下列宣告中，第二個和第三個宣告會產生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="60808-104">In the following declarations, the second and third declarations generate this error.</span></span>  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 <span data-ttu-id="60808-105">第二個宣告會變更原始的一維參數`arrayParam`至陣列的陣列。</span><span class="sxs-lookup"><span data-stu-id="60808-105">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="60808-106">第三個宣告的變更`arrayParam`二維陣列 (rank 2)。</span><span class="sxs-lookup"><span data-stu-id="60808-106">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="60808-107">Visual Basic 可讓多載，可以僅由其中一個這些變更與不同，這類多載不符合[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3)（cls） 標準。</span><span class="sxs-lookup"><span data-stu-id="60808-107">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span></span>  
  
 <span data-ttu-id="60808-108">將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。</span><span class="sxs-lookup"><span data-stu-id="60808-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="60808-109">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="60808-109">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="60808-110">如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="60808-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="60808-111">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="60808-111">By default, this message is a warning.</span></span> <span data-ttu-id="60808-112">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="60808-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="60808-113">**錯誤 ID:** BC40035</span><span class="sxs-lookup"><span data-stu-id="60808-113">**Error ID:** BC40035</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="60808-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="60808-114">To correct this error</span></span>  
  
-   <span data-ttu-id="60808-115">如果您需要 cls 符合性，定義您的多載，可以只將這個說明網頁所提到的變更的多種方式方面與彼此不同。</span><span class="sxs-lookup"><span data-stu-id="60808-115">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>  
  
-   <span data-ttu-id="60808-116">如果您需要的多載的差別，只要在此說明所提到的變更頁面中，移除<xref:System.CLSCompliantAttribute>從其定義或將它們標記為`<CLSCompliant(False)>`。</span><span class="sxs-lookup"><span data-stu-id="60808-116">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60808-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60808-117">See Also</span></span>  
 [<span data-ttu-id="60808-118">\<PAVE OVER > 撰寫符合 CLS 標準的程式碼</span><span class="sxs-lookup"><span data-stu-id="60808-118">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)  
 [<span data-ttu-id="60808-119">程序多載化</span><span class="sxs-lookup"><span data-stu-id="60808-119">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [<span data-ttu-id="60808-120">多載</span><span class="sxs-lookup"><span data-stu-id="60808-120">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)

---
title: 在匯入指定的命名空間或類型&#39;&lt;限定&gt;&#39;不&#39;t 包含任何 public 成員，或找不到
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 21c0794fb4ed6104204fba5d49e37394eff24865
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552134"
---
# <a name="namespace-or-type-specified-in-the-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="56954-102">在匯入指定的命名空間或類型&#39;&lt;限定&gt;&#39;不&#39;t 包含任何 public 成員，或找不到</span><span class="sxs-lookup"><span data-stu-id="56954-102">Namespace or type specified in the Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found</span></span>
<span data-ttu-id="56954-103">中的匯入的命名空間或類型指定\<完整項目名稱 >' 不包含任何 public 成員，或是找不到。</span><span class="sxs-lookup"><span data-stu-id="56954-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="56954-104">請確定命名空間或類型定義，而且包含至少一個 public 成員。</span><span class="sxs-lookup"><span data-stu-id="56954-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="56954-105">請確定別名名稱不包含其他別名。</span><span class="sxs-lookup"><span data-stu-id="56954-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="56954-106">`Imports`陳述式會指定包含的項目不能找到，或未定義任何`Public`成員。</span><span class="sxs-lookup"><span data-stu-id="56954-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="56954-107">A*包含項目的*可以是命名空間、 類別、 結構、 模組、 介面或列舉型別。</span><span class="sxs-lookup"><span data-stu-id="56954-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="56954-108">包含的項目包含成員，例如變數、 程序或其他內含項目。</span><span class="sxs-lookup"><span data-stu-id="56954-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="56954-109">匯入的目的是允許您存取命名空間或類型成員的程式碼，而不必加以限定。</span><span class="sxs-lookup"><span data-stu-id="56954-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="56954-110">若要加入的命名空間或類型的參考，可能也需要您的專案。</span><span class="sxs-lookup"><span data-stu-id="56954-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="56954-111">如需詳細資訊，請參閱 < 匯入包含項目 」 中[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="56954-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="56954-112">如果編譯器找不到指定的包含項目，所以無法解析使用它的參考。</span><span class="sxs-lookup"><span data-stu-id="56954-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="56954-113">如果它找到的項目，但項目不會公開任何`Public`成員，則任何參考可成功。</span><span class="sxs-lookup"><span data-stu-id="56954-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="56954-114">在任一情況下它是無意義的匯入之項目的項目。</span><span class="sxs-lookup"><span data-stu-id="56954-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="56954-115">請記住，如果您匯入包含項目，並將匯入別名指派給它，則您無法使用該匯入別名匯入另一個項目。</span><span class="sxs-lookup"><span data-stu-id="56954-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="56954-116">下列程式碼會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="56954-116">The following code generates a compiler error.</span></span>  
  
 <span data-ttu-id="56954-117">`Imports`   `winfrm`   `= System.Windows.Forms`</span><span class="sxs-lookup"><span data-stu-id="56954-117">`Imports`   `winfrm`   `= System.Windows.Forms`</span></span>  
  
 <span data-ttu-id="56954-118">`' The following statement is`   `INVALID`   `because it reuses an import alias.`</span><span class="sxs-lookup"><span data-stu-id="56954-118">`' The following statement is`   `INVALID`   `because it reuses an import alias.`</span></span>  
  
 <span data-ttu-id="56954-119">`Imports behav =`   `winfrm`  `.Design.Behavior`</span><span class="sxs-lookup"><span data-stu-id="56954-119">`Imports behav =`   `winfrm`  `.Design.Behavior`</span></span>  
  
 <span data-ttu-id="56954-120">**錯誤 ID:** BC40056</span><span class="sxs-lookup"><span data-stu-id="56954-120">**Error ID:** BC40056</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="56954-121">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="56954-121">To correct this error</span></span>  
  
1.  <span data-ttu-id="56954-122">請確認包含的項目是從您的專案存取。</span><span class="sxs-lookup"><span data-stu-id="56954-122">Verify that the containing element is accessible from your project.</span></span>  
  
2.  <span data-ttu-id="56954-123">請確認包含的項目規格不會包含從另一個匯入任何匯入別名。</span><span class="sxs-lookup"><span data-stu-id="56954-123">Verify that the specification of the containing element does not include any import alias from another import.</span></span>  
  
3.  <span data-ttu-id="56954-124">請確認包含的項目會公開至少一個`Public`成員。</span><span class="sxs-lookup"><span data-stu-id="56954-124">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56954-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56954-125">See also</span></span>
- [<span data-ttu-id="56954-126">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="56954-126">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="56954-127">Namespace 陳述式</span><span class="sxs-lookup"><span data-stu-id="56954-127">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="56954-128">Public</span><span class="sxs-lookup"><span data-stu-id="56954-128">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="56954-129">在 Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="56954-129">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="56954-130">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="56954-130">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

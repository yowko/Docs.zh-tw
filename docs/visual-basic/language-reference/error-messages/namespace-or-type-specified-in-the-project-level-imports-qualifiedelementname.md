---
title: 專案層級 Imports '<qualifiedelementname>' 中指定的命名空間或類型不包含任何 Public 成員，或是找不到該命名空間或類型
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 554300f87dbfca351ebcd2d544051968e84880ab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816798"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="00a4d-102">在專案層級 Imports' 中指定的命名空間或類型\<完整項目名稱 >' 不包含任何 public 成員，或是找不到</span><span class="sxs-lookup"><span data-stu-id="00a4d-102">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>
<span data-ttu-id="00a4d-103">在專案層級 Imports' 中指定的命名空間或類型\<完整項目名稱 >' 不包含任何 public 成員，或是找不到。</span><span class="sxs-lookup"><span data-stu-id="00a4d-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="00a4d-104">請確定命名空間或類型定義，而且包含至少一個 public 成員。</span><span class="sxs-lookup"><span data-stu-id="00a4d-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="00a4d-105">請確定別名名稱不包含其他別名。</span><span class="sxs-lookup"><span data-stu-id="00a4d-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="00a4d-106">專案匯入屬性會指定包含的項目不能找到，或未定義任何`Public`成員。</span><span class="sxs-lookup"><span data-stu-id="00a4d-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="00a4d-107">A*包含項目的*可以是命名空間、 類別、 結構、 模組、 介面或列舉型別。</span><span class="sxs-lookup"><span data-stu-id="00a4d-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="00a4d-108">包含的項目包含成員，例如變數、 程序或其他內含項目。</span><span class="sxs-lookup"><span data-stu-id="00a4d-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="00a4d-109">匯入的目的是允許您存取命名空間或類型成員的程式碼，而不必加以限定。</span><span class="sxs-lookup"><span data-stu-id="00a4d-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="00a4d-110">若要加入的命名空間或類型的參考，可能也需要您的專案。</span><span class="sxs-lookup"><span data-stu-id="00a4d-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="00a4d-111">如需詳細資訊，請參閱 < 匯入包含項目 」 中[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="00a4d-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="00a4d-112">如果編譯器找不到指定的包含項目，所以無法解析使用它的參考。</span><span class="sxs-lookup"><span data-stu-id="00a4d-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="00a4d-113">如果它找到的項目，但項目不會公開任何`Public`成員，則任何參考可成功。</span><span class="sxs-lookup"><span data-stu-id="00a4d-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="00a4d-114">在任一情況下它是無意義的匯入之項目的項目。</span><span class="sxs-lookup"><span data-stu-id="00a4d-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="00a4d-115">您使用**專案設計工具**指定匯入的項目。</span><span class="sxs-lookup"><span data-stu-id="00a4d-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="00a4d-116">使用**匯入命名空間**一節**參考**頁面。</span><span class="sxs-lookup"><span data-stu-id="00a4d-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="00a4d-117">您可以前往**專案設計工具**按兩下**我的專案**中的圖示**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="00a4d-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="00a4d-118">**錯誤 ID:** BC40057</span><span class="sxs-lookup"><span data-stu-id="00a4d-118">**Error ID:** BC40057</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="00a4d-119">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="00a4d-119">To correct this error</span></span>  
  
1.  <span data-ttu-id="00a4d-120">開啟**專案設計工具**，並切換至**參考**頁面。</span><span class="sxs-lookup"><span data-stu-id="00a4d-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>  
  
2.  <span data-ttu-id="00a4d-121">在 **匯入命名空間**區段中，確認包含的項目是從您的專案存取。</span><span class="sxs-lookup"><span data-stu-id="00a4d-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>  
  
3.  <span data-ttu-id="00a4d-122">請確認包含的項目會公開至少一個`Public`成員。</span><span class="sxs-lookup"><span data-stu-id="00a4d-122">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00a4d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00a4d-123">See also</span></span>

- [<span data-ttu-id="00a4d-124">專案設計工具、參考頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00a4d-124">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [<span data-ttu-id="00a4d-125">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="00a4d-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="00a4d-126">Public</span><span class="sxs-lookup"><span data-stu-id="00a4d-126">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="00a4d-127">在 Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="00a4d-127">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="00a4d-128">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="00a4d-128">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

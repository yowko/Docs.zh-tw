---
title: 專案層級 Imports '<qualifiedelementname>' 中指定的命名空間或類型不包含任何 Public 成員，或是找不到該命名空間或類型
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 0ee235252d69e6f77ce53b048f45e73d0969e864
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409448"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="5d356-102">專案層級 Imports '\<qualifiedelementname>' 中指定的命名空間或類型不包含任何 Public 成員，或是找不到該命名空間或類型</span><span class="sxs-lookup"><span data-stu-id="5d356-102">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>
<span data-ttu-id="5d356-103">專案層級匯入 ' ' 中指定的命名空間或類型 \<qualifiedelementname> 不包含任何 public 成員，或找不到。</span><span class="sxs-lookup"><span data-stu-id="5d356-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="5d356-104">請確定已定義命名空間或類型，而且包含至少一個公用成員。</span><span class="sxs-lookup"><span data-stu-id="5d356-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="5d356-105">請確定別名名稱不包含其他別名。</span><span class="sxs-lookup"><span data-stu-id="5d356-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="5d356-106">專案的匯入屬性指定了找不到或未定義任何成員的包含元素 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="5d356-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="5d356-107">*包含元素*可以是命名空間、類別、結構、模組、介面或列舉。</span><span class="sxs-lookup"><span data-stu-id="5d356-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="5d356-108">包含的元素包含成員，例如變數、程式或其他包含專案。</span><span class="sxs-lookup"><span data-stu-id="5d356-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="5d356-109">匯入的目的是要讓您的程式碼可以存取命名空間或類型成員，而不需要限定它們。</span><span class="sxs-lookup"><span data-stu-id="5d356-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="5d356-110">您的專案可能也需要加入命名空間或類型的參考。</span><span class="sxs-lookup"><span data-stu-id="5d356-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="5d356-111">如需詳細資訊，請參閱宣告專案[參考](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)中的「匯入包含元素」。</span><span class="sxs-lookup"><span data-stu-id="5d356-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="5d356-112">如果編譯器找不到指定的包含元素，就無法解析使用它的參考。</span><span class="sxs-lookup"><span data-stu-id="5d356-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="5d356-113">如果找到專案，但元素並未公開任何 `Public` 成員，則不會有任何參考成功。</span><span class="sxs-lookup"><span data-stu-id="5d356-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="5d356-114">在任一情況下，匯入元素都沒有意義。</span><span class="sxs-lookup"><span data-stu-id="5d356-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="5d356-115">您可以使用 [**專案設計**工具] 來指定要匯入的元素。</span><span class="sxs-lookup"><span data-stu-id="5d356-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="5d356-116">使用 [**參考**] 頁面的 [匯**入的命名空間**] 區段。</span><span class="sxs-lookup"><span data-stu-id="5d356-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="5d356-117">按兩下**方案總管**中的 [**我的專案**] 圖示，即可進入 [**專案設計**工具]。</span><span class="sxs-lookup"><span data-stu-id="5d356-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="5d356-118">**錯誤識別碼：** BC40057</span><span class="sxs-lookup"><span data-stu-id="5d356-118">**Error ID:** BC40057</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5d356-119">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="5d356-119">To correct this error</span></span>  
  
1. <span data-ttu-id="5d356-120">開啟 [**專案設計**工具]，並切換至 [**參考**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="5d356-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>  
  
2. <span data-ttu-id="5d356-121">在 [匯**入的命名空間**] 區段中，確認可從您的專案存取包含的元素。</span><span class="sxs-lookup"><span data-stu-id="5d356-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>  
  
3. <span data-ttu-id="5d356-122">請確認包含的元素至少會公開一個 `Public` 成員。</span><span class="sxs-lookup"><span data-stu-id="5d356-122">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d356-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d356-123">See also</span></span>

- [<span data-ttu-id="5d356-124">專案設計工具，參考頁 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d356-124">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [<span data-ttu-id="5d356-125">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="5d356-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="5d356-126">公開</span><span class="sxs-lookup"><span data-stu-id="5d356-126">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="5d356-127">Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="5d356-127">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="5d356-128">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="5d356-128">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

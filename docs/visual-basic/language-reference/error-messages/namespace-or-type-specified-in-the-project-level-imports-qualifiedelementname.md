---
title: "命名空間或專案層級 Imports &#39; 中指定的類型&lt;完整項目名稱&gt;&#39; 沒有 &#39; t 包含任何 public 成員，或找不到"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords: BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d0a164562524af239b3b130f681dbc6eff23814
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="47ab1-102">命名空間或專案層級 Imports &#39; 中指定的類型&lt;完整項目名稱&gt;&#39; 沒有 &#39; t 包含任何 public 成員，或找不到</span><span class="sxs-lookup"><span data-stu-id="47ab1-102">Namespace or type specified in the project-level Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found</span></span>
<span data-ttu-id="47ab1-103">在專案層級 Imports' 中指定的命名空間或類型\<完整項目名稱 >' 不包含任何 public 成員，或是找不到。</span><span class="sxs-lookup"><span data-stu-id="47ab1-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="47ab1-104">請確定命名空間或類型已定義，而且包含至少一個 public 成員。</span><span class="sxs-lookup"><span data-stu-id="47ab1-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="47ab1-105">請確定別名名稱不包含其他別名。</span><span class="sxs-lookup"><span data-stu-id="47ab1-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="47ab1-106">專案匯入屬性會指定包含的項目，或是無法找到未定義任何`Public`成員。</span><span class="sxs-lookup"><span data-stu-id="47ab1-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="47ab1-107">A*包含項目的*可以是命名空間、 類別、 結構、 模組、 介面或列舉型別。</span><span class="sxs-lookup"><span data-stu-id="47ab1-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="47ab1-108">包含的項目包含成員，例如變數、 程序或其他內含項目。</span><span class="sxs-lookup"><span data-stu-id="47ab1-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="47ab1-109">匯入的目的是允許您存取命名空間或類型成員的程式碼，而不必加以限定。</span><span class="sxs-lookup"><span data-stu-id="47ab1-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="47ab1-110">若要加入的命名空間或類型的參考，可能也需要您的專案。</span><span class="sxs-lookup"><span data-stu-id="47ab1-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="47ab1-111">如需詳細資訊，請參閱 < 匯入包含項目 >[宣告之項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="47ab1-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="47ab1-112">如果編譯器找不到指定的包含項目，它無法解析使用它的參考。</span><span class="sxs-lookup"><span data-stu-id="47ab1-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="47ab1-113">如果它找到的項目但項目不會公開任何`Public`成員，則任何參考可以成功。</span><span class="sxs-lookup"><span data-stu-id="47ab1-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="47ab1-114">在任一情況下是無意義的匯入的項目。</span><span class="sxs-lookup"><span data-stu-id="47ab1-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="47ab1-115">您使用**專案設計工具**來指定匯入的項目。</span><span class="sxs-lookup"><span data-stu-id="47ab1-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="47ab1-116">使用**匯入命名空間**區段**參考**頁面。</span><span class="sxs-lookup"><span data-stu-id="47ab1-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="47ab1-117">您可以取得**專案設計工具**按兩下**我的專案**中的圖示**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="47ab1-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="47ab1-118">**錯誤 ID:** BC40057</span><span class="sxs-lookup"><span data-stu-id="47ab1-118">**Error ID:** BC40057</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="47ab1-119">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="47ab1-119">To correct this error</span></span>  
  
1.  <span data-ttu-id="47ab1-120">開啟**專案設計工具**並切換至**參考**頁面。</span><span class="sxs-lookup"><span data-stu-id="47ab1-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>  
  
2.  <span data-ttu-id="47ab1-121">在**匯入命名空間**區段中，確認包含的項目從您的專案可以存取。</span><span class="sxs-lookup"><span data-stu-id="47ab1-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>  
  
3.  <span data-ttu-id="47ab1-122">請確認包含的項目會公開至少一個`Public`成員。</span><span class="sxs-lookup"><span data-stu-id="47ab1-122">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47ab1-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47ab1-123">See Also</span></span>  
 [<span data-ttu-id="47ab1-124">專案設計工具、參考頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47ab1-124">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)  
 [<span data-ttu-id="47ab1-125">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="47ab1-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="47ab1-126">Public</span><span class="sxs-lookup"><span data-stu-id="47ab1-126">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="47ab1-127">在 Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="47ab1-127">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="47ab1-128">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="47ab1-128">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

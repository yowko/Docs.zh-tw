---
title: 如何：在 Visual Studio 中建立 LINQ to DataSet 專案
ms.date: 03/30/2017
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 094d766146fe55a865713a4672a2bee6a838ff55
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758863"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="c6d32-102">如何：在 Visual Studio 中建立 LINQ to DataSet 專案</span><span class="sxs-lookup"><span data-stu-id="c6d32-102">How to: Create a LINQ to DataSet Project In Visual Studio</span></span>
<span data-ttu-id="c6d32-103">不同的 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 專案類型需要特定匯入的命名空間 (Namespace) (Visual Basic) 或 `using` 指示詞 (C#) 和參考。</span><span class="sxs-lookup"><span data-stu-id="c6d32-103">The different types of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] projects require certain imported namespaces (Visual Basic) or `using` directives (C#) and references.</span></span> <span data-ttu-id="c6d32-104">最小需求是 System.Core.dll 的參考和 `using` 的 <xref:System.Linq> 指示詞。</span><span class="sxs-lookup"><span data-stu-id="c6d32-104">The minimum requirement is a reference to System.Core.dll and a `using` directive for <xref:System.Linq>.</span></span> <span data-ttu-id="c6d32-105">根據預設，如果您建立新的 [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] 專案，系統就會提供這些項目。</span><span class="sxs-lookup"><span data-stu-id="c6d32-105">By default, these are supplied if you create a new [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] project.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="c6d32-106"> 也需要 System.Data.dll 和 System.Data.DataSetExtensions.dll 的參考以及 `Imports` (Visual Basic) 或 `using` (C#) 指示詞。</span><span class="sxs-lookup"><span data-stu-id="c6d32-106"> also requires a reference to System.Data.dll and System.Data.DataSetExtensions.dll and an `Imports` (Visual Basic) or `using` (C#) directive.</span></span>  
  
 <span data-ttu-id="c6d32-107">如果您要從舊版 Visual Studio 升級專案，可能必須手動提供這些 LINQ 相關的參考。</span><span class="sxs-lookup"><span data-stu-id="c6d32-107">If you are upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span> <span data-ttu-id="c6d32-108">此外，您可能也必須手動將專案設定為以 .NET Framework 3.5 版為目標。</span><span class="sxs-lookup"><span data-stu-id="c6d32-108">You might also have to manually set the project to target the .NET Framework version 3.5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6d32-109">如果您要從命令提示字元建置，您必須手動參考中的 LINQ 相關 Dll `drive` **:** \program Assemblies\Microsoft\Framework\v3.5。</span><span class="sxs-lookup"><span data-stu-id="c6d32-109">If you are building from a command prompt, you must manually reference the LINQ-related DLLs in `drive`**:** \Program Files\Reference Assemblies\Microsoft\Framework\v3.5.</span></span>  
  
### <a name="to-target-the-net-framework-35"></a><span data-ttu-id="c6d32-110">以 .NET Framework 3.5 為目標</span><span class="sxs-lookup"><span data-stu-id="c6d32-110">To target the .NET Framework 3.5</span></span>  
  
1.  <span data-ttu-id="c6d32-111">在 [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] 中，建立新的 Visual Basic 或 C# 專案。</span><span class="sxs-lookup"><span data-stu-id="c6d32-111">In [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], create a new Visual Basic or C# project.</span></span> <span data-ttu-id="c6d32-112">或者，您也可以開啟在 Visual Studio 2005 中建立的 Visual Basic 或 C# 專案，然後遵循提示，將它轉換成 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="c6d32-112">Alternatively, you can open a Visual Basic or C# project that was created in Visual Studio 2005 and follow the prompts to convert it to a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="c6d32-113">C# 專案，請按一下**專案**功能表，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="c6d32-113">For a C# project, click the **Project** menu, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="c6d32-114">在**應用程式**屬性頁上，選取.NET Framework 3.5 中**目標 Framework**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c6d32-114">In the **Application** property page, select .NET Framework 3.5 in the **Target Framework** drop-down list.</span></span>  
  
3.  <span data-ttu-id="c6d32-115">Visual Basic 專案，請按一下**專案**功能表，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="c6d32-115">For a Visual Basic project, click the **Project** menu, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="c6d32-116">在**編譯**屬性頁上，按一下 **進階編譯選項**，然後選取 在.NET Framework 3.5**目標 Framework （所有組態）** 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c6d32-116">In the **Compile** property page, click **Advanced Compile Options** and then select .NET Framework 3.5 in the **Target Framework (all configurations)** drop-down list.</span></span>  
  
4.  <span data-ttu-id="c6d32-117">在**專案**功能表上，按一下 **加入參考**，按一下  **.NET**索引標籤上，向下捲動至**System.Core**，按一下它，然後按  **確定**。</span><span class="sxs-lookup"><span data-stu-id="c6d32-117">On the **Project** menu, click **Add Reference**, click the **.NET** tab, scroll down to **System.Core**, click it, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="c6d32-118">將 `using` 的 <xref:System.Linq> 指示詞或匯入的命名空間加入至您的原始程式碼檔或專案。</span><span class="sxs-lookup"><span data-stu-id="c6d32-118">Add a `using` directive or imported namespace for <xref:System.Linq> to your source code file or project.</span></span>  
  
     <span data-ttu-id="c6d32-119">如需詳細資訊，請參閱[using 指示詞](~/docs/csharp/language-reference/keywords/using-directive.md)或[如何： 加入或移除已匯入命名空間 (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="c6d32-119">For more information, see [using Directive](~/docs/csharp/language-reference/keywords/using-directive.md) or [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
### <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="c6d32-120">若要啟用 LINQ to DataSet 功能</span><span class="sxs-lookup"><span data-stu-id="c6d32-120">To enable LINQ to DataSet functionality</span></span>  
  
1.  <span data-ttu-id="c6d32-121">必要時，請遵循本主題先前的步驟來加入 System.Core.dll 的參考和 System.Linq 的 `using` 指示詞或匯入命名空間。</span><span class="sxs-lookup"><span data-stu-id="c6d32-121">If necessary, follow the steps earlier in this topic to add a reference to System.Core.dll and a `using` directive or imported namespace for System.Linq.</span></span>  
  
2.  <span data-ttu-id="c6d32-122">在 C# 或 Visual Basic 中，按一下**專案**功能表，然後再按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="c6d32-122">In C# or Visual Basic, click the **Project** menu, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="c6d32-123">在**加入參考**對話方塊中，按一下  **.NET**索引標籤上，如果不在最上方。</span><span class="sxs-lookup"><span data-stu-id="c6d32-123">In the **Add Reference** dialog box, click the **.NET** tab if it is not on top.</span></span> <span data-ttu-id="c6d32-124">向下捲動至**System.Data**和**System.Data.DataSetExtensions** ，然後按一下 它們。</span><span class="sxs-lookup"><span data-stu-id="c6d32-124">Scroll down to **System.Data** and **System.Data.DataSetExtensions** and click on them.</span></span> <span data-ttu-id="c6d32-125">按一下**確定** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c6d32-125">Click the **OK** button.</span></span>  
  
4.  <span data-ttu-id="c6d32-126">將 `using` 的 <xref:System.Data> 指示詞或匯入的命名空間加入至您的原始程式碼檔或專案。</span><span class="sxs-lookup"><span data-stu-id="c6d32-126">Add a `using` directive or imported namespace for <xref:System.Data> to your source code file or project.</span></span> <span data-ttu-id="c6d32-127">如需詳細資訊，請參閱[using 指示詞](~/docs/csharp/language-reference/keywords/using-directive.md)或[如何： 加入或移除已匯入命名空間 (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="c6d32-127">For more information, see [using Directive](~/docs/csharp/language-reference/keywords/using-directive.md) or [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
5.  <span data-ttu-id="c6d32-128">針對 LINQ to Dataset 功能，加入 System.Data.DataSetExtensions.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="c6d32-128">Add a reference to System.Data.DataSetExtensions.dll for LINQ to Dataset functionality.</span></span> <span data-ttu-id="c6d32-129">如果 System.Data.dll 的參考原本不存在，請加入這項參考。</span><span class="sxs-lookup"><span data-stu-id="c6d32-129">Add a reference to System.Data.dll if it does not already exist.</span></span>  
  
6.  <span data-ttu-id="c6d32-130">或者，根據您連接至資料庫的方式，加入 `using` 或 `System.Data.Common` 的 `System.Data.SqlClient` 指示詞或匯入的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c6d32-130">Optionally, add a `using` directive or imported namespace for `System.Data.Common` or `System.Data.SqlClient`, depending on how you connect to the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6d32-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6d32-131">See Also</span></span>  
 [<span data-ttu-id="c6d32-132">快速入門</span><span class="sxs-lookup"><span data-stu-id="c6d32-132">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
 [<span data-ttu-id="c6d32-133">LINQ 使用者入門</span><span class="sxs-lookup"><span data-stu-id="c6d32-133">Getting Started with LINQ</span></span>](http://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)

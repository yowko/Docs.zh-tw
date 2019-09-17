---
title: 在 Visual Studio 中建立 LINQ to DataSet 專案
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 8b905c65575c3c567459d843b2a5d1606bc63228
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783772"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="9e7eb-102">HOW TO：在 Visual Studio 中建立 LINQ to DataSet 專案</span><span class="sxs-lookup"><span data-stu-id="9e7eb-102">How to: Create a LINQ to DataSet project In Visual Studio</span></span>

<span data-ttu-id="9e7eb-103">不同類型的 LINQ 專案需要特定的元件參考和匯入的命名空間（  Visual Basic）或C#[使用](../../../csharp/language-reference/keywords/using-directive.md)指示詞（）。</span><span class="sxs-lookup"><span data-stu-id="9e7eb-103">The different types of LINQ projects require certain assembly references and imported namespaces (Visual Basic) or [using](../../../csharp/language-reference/keywords/using-directive.md) directives (C#).</span></span> <span data-ttu-id="9e7eb-104">LINQ 的最低需求是的*system.object*參考和的`using` <xref:System.Linq>指示詞。</span><span class="sxs-lookup"><span data-stu-id="9e7eb-104">The minimum requirement for LINQ is a reference to *System.Core.dll* and a `using` directive for <xref:System.Linq>.</span></span>

<span data-ttu-id="9e7eb-105">如果您在 Visual Studio 2017 中建立新C#的主控台應用程式專案，則預設會提供這些需求。</span><span class="sxs-lookup"><span data-stu-id="9e7eb-105">These requirements are supplied by default if you create a new C# console app project in Visual Studio 2017.</span></span> <span data-ttu-id="9e7eb-106">如果您要從舊版的 Visual Studio 升級專案，您可能必須手動提供這些 LINQ 相關的參考。</span><span class="sxs-lookup"><span data-stu-id="9e7eb-106">If you're upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span>

<span data-ttu-id="9e7eb-107">LINQ to DataSet 需要*system.data.datasetextensions.dll*的兩個額外參考 *，才能進行*。</span><span class="sxs-lookup"><span data-stu-id="9e7eb-107">LINQ to DataSet requires two additional references to *System.Data.dll* and *System.Data.DataSetExtensions.dll*.</span></span>

> [!NOTE]
> <span data-ttu-id="9e7eb-108">如果您是從命令提示字元建立，則必須在 *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*中手動參考 LINQ 相關的 dll。</span><span class="sxs-lookup"><span data-stu-id="9e7eb-108">If you're building from a command prompt, you must manually reference the LINQ-related DLLs in *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span></span>

## <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="9e7eb-109">若要啟用 LINQ to DataSet 功能</span><span class="sxs-lookup"><span data-stu-id="9e7eb-109">To enable LINQ to DataSet functionality</span></span>

<span data-ttu-id="9e7eb-110">請遵循下列步驟，在現有的專案中啟用 LINQ to DataSet 功能。</span><span class="sxs-lookup"><span data-stu-id="9e7eb-110">Follow these steps to enable LINQ to DataSet functionality in an existing project.</span></span>

1. <span data-ttu-id="9e7eb-111">將參考新增至 System.data.datasetextensions.dll.**核心**、 **system. data**和**system.web**。</span><span class="sxs-lookup"><span data-stu-id="9e7eb-111">Add references to **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span>

   <span data-ttu-id="9e7eb-112">在**方案總管**中，以滑鼠右鍵按一下 [**參考**] 節點，然後選取 [**新增參考**]。</span><span class="sxs-lookup"><span data-stu-id="9e7eb-112">In **Solution Explorer**, right-click on the **References** node and select **Add Reference**.</span></span> <span data-ttu-id="9e7eb-113">在 [**參考管理員**] 對話方塊中，**選取 [** System.string]、[ **system.web**] 和 [ **system.data.datasetextensions.dll**]。</span><span class="sxs-lookup"><span data-stu-id="9e7eb-113">In the **Reference Manager** dialog box, select **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span> <span data-ttu-id="9e7eb-114">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9e7eb-114">Select **OK**.</span></span>

1. <span data-ttu-id="9e7eb-115">為**system.web**和 system.string 新增[using](../../../csharp/language-reference/keywords/using-directive.md)指示詞（或匯入 Visual Basic 中的[語句](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) **）。**</span><span class="sxs-lookup"><span data-stu-id="9e7eb-115">Add [using](../../../csharp/language-reference/keywords/using-directive.md) directives (or [Imports statements](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) in Visual Basic) for **System.Data** and **System.Linq**.</span></span>

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. <span data-ttu-id="9e7eb-116">（選擇性）針對`using` [ **SqlClient**] `Imports`加入指示詞（或語句），視您連接到資料庫的方式而**定。**</span><span class="sxs-lookup"><span data-stu-id="9e7eb-116">Optionally, add a `using` directive (or `Imports` statement) for **System.Data.Common** or **System.Data.SqlClient**, depending on how you connect to the database.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e7eb-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e7eb-117">See also</span></span>

- [<span data-ttu-id="9e7eb-118">開始使用 LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="9e7eb-118">Get started with LINQ to DataSet</span></span>](getting-started-linq-to-dataset.md)

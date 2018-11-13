---
title: 建立 LINQ to DataSet 專案在 Visual Studio
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 22763d3b9581d09d7bdda0c09480f8d36bb8e2ec
ms.sourcegitcommit: 4bca8f7e172fd019ef437a4803bf5895c6bc4781
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2018
ms.locfileid: "50980725"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="0a205-102">如何： 建立 LINQ to DataSet 專案在 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0a205-102">How to: Create a LINQ to DataSet project In Visual Studio</span></span>

<span data-ttu-id="0a205-103">LINQ 專案的不同類型需要特定的組件參考和匯入的命名空間 (Visual Basic) 或[使用](../../../csharp/language-reference/keywords/using-directive.md)指示詞 (C#)。</span><span class="sxs-lookup"><span data-stu-id="0a205-103">The different types of LINQ projects require certain assembly references and imported namespaces (Visual Basic) or [using](../../../csharp/language-reference/keywords/using-directive.md) directives (C#).</span></span> <span data-ttu-id="0a205-104">LINQ 的最低需求是參考*System.Core.dll*並`using`指示詞<xref:System.Linq>。</span><span class="sxs-lookup"><span data-stu-id="0a205-104">The minimum requirement for LINQ is a reference to *System.Core.dll* and a `using` directive for <xref:System.Linq>.</span></span>

<span data-ttu-id="0a205-105">如果您在 Visual Studio 2017 中建立的新 C# 主控台應用程式專案預設會提供這些需求。</span><span class="sxs-lookup"><span data-stu-id="0a205-105">These requirements are supplied by default if you create a new C# console app project in Visual Studio 2017.</span></span> <span data-ttu-id="0a205-106">如果您要從舊版的 Visual Studio 升級專案，您可能必須以手動方式提供這些 LINQ 相關參考。</span><span class="sxs-lookup"><span data-stu-id="0a205-106">If you're upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span>

<span data-ttu-id="0a205-107">LINQ to DataSet 需要兩個額外參考*System.Data.dll*並*System.Data.DataSetExtensions.dll*。</span><span class="sxs-lookup"><span data-stu-id="0a205-107">LINQ to DataSet requires two additional references to *System.Data.dll* and *System.Data.DataSetExtensions.dll*.</span></span>

> [!NOTE]
> <span data-ttu-id="0a205-108">如果您要從命令提示字元建置，就必須手動參考中的 LINQ 相關 Dll *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*。</span><span class="sxs-lookup"><span data-stu-id="0a205-108">If you're building from a command prompt, you must manually reference the LINQ-related DLLs in *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span></span>

## <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="0a205-109">若要啟用 LINQ to DataSet 功能</span><span class="sxs-lookup"><span data-stu-id="0a205-109">To enable LINQ to DataSet functionality</span></span>

<span data-ttu-id="0a205-110">請遵循下列步驟來啟用 LINQ to DataSet 功能，在現有的專案。</span><span class="sxs-lookup"><span data-stu-id="0a205-110">Follow these steps to enable LINQ to DataSet functionality in an existing project.</span></span>

1. <span data-ttu-id="0a205-111">將參考加入至**System.Core**， **System.Data**，並**System.Data.DataSetExtensions**。</span><span class="sxs-lookup"><span data-stu-id="0a205-111">Add references to **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span>

   <span data-ttu-id="0a205-112">在 [**方案總管] 中**，以滑鼠右鍵按一下**參考**節點，然後選取**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="0a205-112">In **Solution Explorer**, right-click on the **References** node and select **Add Reference**.</span></span> <span data-ttu-id="0a205-113">在 **參考管理員**對話方塊中，選取**System.Core**， **System.Data**，以及**System.Data.DataSetExtensions**。</span><span class="sxs-lookup"><span data-stu-id="0a205-113">In the **Reference Manager** dialog box, select **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span> <span data-ttu-id="0a205-114">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="0a205-114">Select **OK**.</span></span>

1. <span data-ttu-id="0a205-115">新增[使用](../../../csharp/language-reference/keywords/using-directive.md)指示詞 (或[Imports 陳述式](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)Visual Basic 中) 的**System.Data**並**System.Linq**。</span><span class="sxs-lookup"><span data-stu-id="0a205-115">Add [using](../../../csharp/language-reference/keywords/using-directive.md) directives (or [Imports statements](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) in Visual Basic) for **System.Data** and **System.Linq**.</span></span>

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. <span data-ttu-id="0a205-116">（選擇性） 加入`using`指示詞 (或`Imports`陳述式) 的**System.Data.Common**或是**System.Data.SqlClient**，取決於連接到資料庫的方式。</span><span class="sxs-lookup"><span data-stu-id="0a205-116">Optionally, add a `using` directive (or `Imports` statement) for **System.Data.Common** or **System.Data.SqlClient**, depending on how you connect to the database.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a205-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a205-117">See also</span></span>

- [<span data-ttu-id="0a205-118">開始使用 LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="0a205-118">Get started with LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)

---
title: 來源連結與 .NET 程式庫
description: 使用來源連結改善 .NET 程式庫偵錯的最佳做法建議。
ms.date: 01/15/2019
ms.openlocfilehash: 3d768ae6e79efa23a8402ea37bc34cd58cd52c8c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744547"
---
# <a name="source-link"></a><span data-ttu-id="dc6b8-103">來源連結</span><span class="sxs-lookup"><span data-stu-id="dc6b8-103">Source Link</span></span>

<span data-ttu-id="dc6b8-104">來源連結技術可讓開發人員對來自 NuGet 的 .NET 組件進行原始程式碼偵錯。</span><span class="sxs-lookup"><span data-stu-id="dc6b8-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="dc6b8-105">來源連結會在建立 NuGet 套件時執行，並將原始程式碼控制中繼資料內嵌在組件和套件。</span><span class="sxs-lookup"><span data-stu-id="dc6b8-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="dc6b8-106">下載套件並在 Visual Studio 中啟用來源連結的開發人員可以逐步執行原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="dc6b8-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="dc6b8-107">來源連結提供原始程式碼控制中繼資料來建立絕佳的偵錯體驗。</span><span class="sxs-lookup"><span data-stu-id="dc6b8-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="dc6b8-108">來源連結示範</span><span class="sxs-lookup"><span data-stu-id="dc6b8-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="dc6b8-109">使用來源連結</span><span class="sxs-lookup"><span data-stu-id="dc6b8-109">Using Source Link</span></span>

<span data-ttu-id="dc6b8-110">使用來源連結的指示位於 [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub 存放庫。</span><span class="sxs-lookup"><span data-stu-id="dc6b8-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="dc6b8-111">您可以使用 [NuGet 套件總管](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer)確認來源連結中繼資料已成功內嵌在套件中。</span><span class="sxs-lookup"><span data-stu-id="dc6b8-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="dc6b8-112">檢查具有認可識別碼的 `Repository` 中繼資料是否存在，而且 .pdb 檔案會與每個目標的 .dll 一併找到。</span><span class="sxs-lookup"><span data-stu-id="dc6b8-112">Check the `Repository` metadata is present with a commit identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="dc6b8-113">![NuGet 封裝瀏覽器中的來源連結](./media/sourcelink/nuget-package-explorer-sourcelink.png "NuGet 封裝瀏覽器中的來源連結")</span><span class="sxs-lookup"><span data-stu-id="dc6b8-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="dc6b8-114">✔️考慮使用來源連結，將原始檔控制中繼資料新增至您的元件和 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="dc6b8-114">✔️ CONSIDER using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="dc6b8-115">您可以將偵錯工具屬性新增至您的類型，進一步加強開發人員的偵錯體驗。</span><span class="sxs-lookup"><span data-stu-id="dc6b8-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
>
> * <span data-ttu-id="dc6b8-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> 可以自訂類別或欄位在偵錯工具變數視窗中顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="dc6b8-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="dc6b8-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> 指示偵錯工具逐步執行程式碼，而不要進入程式碼。</span><span class="sxs-lookup"><span data-stu-id="dc6b8-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="dc6b8-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> 控制成員是否要顯示在偵錯工具變數視窗中。</span><span class="sxs-lookup"><span data-stu-id="dc6b8-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="dc6b8-119">✔️考慮發佈符號檔（`*.pdb`）。</span><span class="sxs-lookup"><span data-stu-id="dc6b8-119">✔️ CONSIDER publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="dc6b8-120">如需最佳偵錯體驗，您的程式庫應該發佈符號檔，以及使用來源連結。</span><span class="sxs-lookup"><span data-stu-id="dc6b8-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="dc6b8-121">如需有關符號檔和符號套件的詳細資訊，請參閱[符號套件](./nuget.md#symbol-packages)。</span><span class="sxs-lookup"><span data-stu-id="dc6b8-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="dc6b8-122">[上一頁](dependencies.md)
>[下一頁](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="dc6b8-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>

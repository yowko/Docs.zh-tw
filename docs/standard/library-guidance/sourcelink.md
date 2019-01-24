---
title: SourceLink 與 .NET 程式庫
description: 使用 SourceLink 改善 .NET 程式庫偵錯的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: be97f868e2fcfc6c45e4bbac45b033f8914f4d99
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333534"
---
# <a name="sourcelink"></a><span data-ttu-id="e251e-103">SourceLink</span><span class="sxs-lookup"><span data-stu-id="e251e-103">SourceLink</span></span>

<span data-ttu-id="e251e-104">SourceLink 技術可讓開發人員對來自 NuGet 的 .NET 組件進行原始程式碼偵錯。</span><span class="sxs-lookup"><span data-stu-id="e251e-104">SourceLink is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="e251e-105">SourceLink 會在建立 NuGet 套件時執行，並將原始程式碼控制中繼資料內嵌在組件和套件。</span><span class="sxs-lookup"><span data-stu-id="e251e-105">SourceLink executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="e251e-106">下載套件並在 Visual Studio 中啟用 SourceLink 的開發人員可以逐步執行原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="e251e-106">Developers who download the package and have SourceLink enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="e251e-107">SourceLink 提供原始程式碼控制中繼資料來建立絕佳的偵錯體驗。</span><span class="sxs-lookup"><span data-stu-id="e251e-107">SourceLink provides source control metadata to create a great debugging experience.</span></span>

## <a name="sourcelink-demo"></a><span data-ttu-id="e251e-108">SourceLink 示範</span><span class="sxs-lookup"><span data-stu-id="e251e-108">SourceLink demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a><span data-ttu-id="e251e-109">使用 SourceLink</span><span class="sxs-lookup"><span data-stu-id="e251e-109">Using SourceLink</span></span>

<span data-ttu-id="e251e-110">使用 SourceLink 的指示位於 [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub 存放庫。</span><span class="sxs-lookup"><span data-stu-id="e251e-110">Instructions for using SourceLink can be found on the [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="e251e-111">您可以使用 [NuGet 套件總管](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer)確認 SourceLink 中繼資料已成功內嵌在套件中。</span><span class="sxs-lookup"><span data-stu-id="e251e-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the SourceLink metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="e251e-112">確認 `Repository` 中繼資料存在並具有註解識別碼，且 .pdb 檔案與每個目標的 .dll 在一起。</span><span class="sxs-lookup"><span data-stu-id="e251e-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="e251e-113">![NuGet 套件總管中的 SourceLink](./media/sourcelink/nuget-package-explorer-sourcelink.png "NuGet 套件總管中的 SourceLink")</span><span class="sxs-lookup"><span data-stu-id="e251e-113">![SourceLink in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink in NuGet Package Explorer")</span></span>

<span data-ttu-id="e251e-114">**✔️ 請考慮**使用 SourceLink 以將原始程式碼控制中繼資料新增到您的組件與 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="e251e-114">**✔️ CONSIDER** using SourceLink to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="e251e-115">您可以將偵錯工具屬性新增至您的類型，進一步加強開發人員的偵錯體驗。</span><span class="sxs-lookup"><span data-stu-id="e251e-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
> * <span data-ttu-id="e251e-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> 可以自訂類別或欄位在偵錯工具變數視窗中顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="e251e-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="e251e-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> 指示偵錯工具逐步執行程式碼，而不要進入程式碼。</span><span class="sxs-lookup"><span data-stu-id="e251e-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="e251e-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> 控制成員是否要顯示在偵錯工具變數視窗中。</span><span class="sxs-lookup"><span data-stu-id="e251e-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="e251e-119">**✔️ CONSIDER**發行符號檔 (`*.pdb`)。</span><span class="sxs-lookup"><span data-stu-id="e251e-119">**✔️ CONSIDER** publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="e251e-120">如需有關符號檔和符號套件的詳細資訊，請參閱[符號套件](./nuget.md#symbol-packages)。</span><span class="sxs-lookup"><span data-stu-id="e251e-120">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e251e-121">[上一頁](dependencies.md)
>[下一頁](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="e251e-121">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>

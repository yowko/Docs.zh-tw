---
title: SourceLink 和.NET 程式庫
description: 使用 SourceLink 改善偵錯.NET 程式庫的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: fa4af47eaa5dd1510640c2bf0ebb2187b56efae0
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49369795"
---
# <a name="sourcelink"></a><span data-ttu-id="7cb3b-103">SourceLink</span><span class="sxs-lookup"><span data-stu-id="7cb3b-103">SourceLink</span></span>

<span data-ttu-id="7cb3b-104">SourceLink 是一種技術，可讓來自 NuGet 的開發人員的.NET 組件的偵錯的來源的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7cb3b-104">SourceLink is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="7cb3b-105">SourceLink 執行時建立 NuGet 套件，並將內嵌在組件和封裝的來源控制中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7cb3b-105">SourceLink executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="7cb3b-106">開發人員下載封裝，並已在 Visual Studio 中啟用的 SourceLink 可以逐步執行原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="7cb3b-106">Developers who download the package and have SourceLink enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="7cb3b-107">SourceLink 提供來源控制項的中繼資料來建立絕佳的偵錯體驗。</span><span class="sxs-lookup"><span data-stu-id="7cb3b-107">SourceLink provides source control metadata to create a great debugging experience.</span></span>

## <a name="sourcelink-demo"></a><span data-ttu-id="7cb3b-108">SourceLink 示範</span><span class="sxs-lookup"><span data-stu-id="7cb3b-108">SourceLink demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a><span data-ttu-id="7cb3b-109">使用 SourceLink</span><span class="sxs-lookup"><span data-stu-id="7cb3b-109">Using SourceLink</span></span>

<span data-ttu-id="7cb3b-110">使用 SourceLink 指示可於[dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub 存放庫。</span><span class="sxs-lookup"><span data-stu-id="7cb3b-110">Instructions for using SourceLink can be found on the [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="7cb3b-111">您可以使用[NuGet 套件總管](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer)確認 SourceLink 中繼資料包含在封裝中成功內嵌。</span><span class="sxs-lookup"><span data-stu-id="7cb3b-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the SourceLink metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="7cb3b-112">檢查`Repository`中繼資料存在於註解識別碼和.pdb 檔案的位置與每個目標的.dll。</span><span class="sxs-lookup"><span data-stu-id="7cb3b-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="7cb3b-113">![在 [NuGet 套件總管] 的 SourceLink](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink NuGet 封裝總管 中")</span><span class="sxs-lookup"><span data-stu-id="7cb3b-113">![SourceLink in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink in NuGet Package Explorer")</span></span>

<span data-ttu-id="7cb3b-114">**請考慮 ✔️**使用 SourceLink 將原始檔控制中繼資料新增至您的組件和 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="7cb3b-114">**✔️ CONSIDER** using SourceLink to add source control metadata to your assemblies and NuGet package.</span></span>

<span data-ttu-id="7cb3b-115">**請考慮 ✔️** PDB 檔納入 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="7cb3b-115">**✔️ CONSIDER** including PDB files in the NuGet package.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="7cb3b-116">[上一頁](./dependencies.md)
[下一頁](./publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="7cb3b-116">[Previous](./dependencies.md)
[Next](./publish-nuget-package.md)</span></span>

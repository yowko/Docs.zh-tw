---
title: NETSDK1004：找不到資產檔案
description: 瞭解在找不到檔案上的 project.assets.js時，所發生的 .NET SDK 錯誤 NETSDK1004。
ms.topic: error-reference
ms.date: 01/29/2021
f1_keywords:
- NETSDK1004
ms.openlocfilehash: 8416063fe318106cbcb4dbccacef3ecaaff5bba2
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216431"
---
# <a name="netsdk1004-assets-file-not-found"></a><span data-ttu-id="e3d5a-103">NETSDK1004：找不到資產檔案</span><span class="sxs-lookup"><span data-stu-id="e3d5a-103">NETSDK1004: Assets file not found</span></span>

<span data-ttu-id="e3d5a-104">本文 **適用于：** ✔️ .net CORE 2.1.100 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="e3d5a-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="e3d5a-105">NuGet 會在 *obj* 資料夾中，將名為 *project.assets.js* 的檔案寫入，而 .net SDK 會使用它來取得封裝的相關資訊，以傳遞至編譯器。</span><span class="sxs-lookup"><span data-stu-id="e3d5a-105">NuGet writes a file named *project.assets.json* in the *obj* folder, and the .NET SDK uses it to get information about packages to pass into the compiler.</span></span> <span data-ttu-id="e3d5a-106">在組建期間找不到資產檔案 *project.assets.js* 時，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="e3d5a-106">This error occurs when the assets file *project.assets.json* is not found during build.</span></span> <span data-ttu-id="e3d5a-107">完整的錯誤訊息與下列範例類似：</span><span class="sxs-lookup"><span data-stu-id="e3d5a-107">The full error message is similar to the following example:</span></span>

<span data-ttu-id="e3d5a-108">**NETSDK1004：找不到資產檔案「C:\path\to\project.assets.js開啟」。執行 NuGet 套件還原，以產生此檔案。**</span><span class="sxs-lookup"><span data-stu-id="e3d5a-108">**NETSDK1004: Assets file 'C:\path\to\project.assets.json' not found. Run a NuGet package restore to generate this file.**</span></span>

<span data-ttu-id="e3d5a-109">以下是一些可能的錯誤原因：</span><span class="sxs-lookup"><span data-stu-id="e3d5a-109">Here are some possible causes of the error:</span></span>

* <span data-ttu-id="e3d5a-110">您正在 `dotnet build` 從包含字元的目錄路徑中執行命令 `%` 。</span><span class="sxs-lookup"><span data-stu-id="e3d5a-110">You are running the `dotnet build` command from a directory path that contains a `%` character.</span></span> <span data-ttu-id="e3d5a-111">若要解決此錯誤，請 `%` 從資料夾名稱中移除，然後重新執行 `dotnet build` 。</span><span class="sxs-lookup"><span data-stu-id="e3d5a-111">To resolve the error, remove the `%` from the folder name, and rerun `dotnet build`.</span></span>
* <span data-ttu-id="e3d5a-112">專案系統不會自動偵測並還原專案檔的變更。</span><span class="sxs-lookup"><span data-stu-id="e3d5a-112">A change to the project file wasn't automatically detected and restored by the project system.</span></span> <span data-ttu-id="e3d5a-113">若要解決此錯誤，請開啟命令提示字元，然後 `dotnet restore` 在專案上執行。</span><span class="sxs-lookup"><span data-stu-id="e3d5a-113">To resolve the error, open a command prompt and run `dotnet restore` on the project.</span></span>
* <span data-ttu-id="e3d5a-114">專案是由舊版 Nuget.exe 分開還原。</span><span class="sxs-lookup"><span data-stu-id="e3d5a-114">A project was restored separately by an older version of Nuget.exe.</span></span> <span data-ttu-id="e3d5a-115">若要解決此錯誤，請開啟命令提示字元，然後 `dotnet restore` 在專案上執行。</span><span class="sxs-lookup"><span data-stu-id="e3d5a-115">To resolve the error, open a command prompt and run `dotnet restore` on the project.</span></span>
* <span data-ttu-id="e3d5a-116">先前的錯誤（例如 NETSDK1045 (您所使用的 SDK 版本不支援專案的目標 framework) ，因此無法建立專案資產檔案。</span><span class="sxs-lookup"><span data-stu-id="e3d5a-116">An earlier error, such as NETSDK1045 (the version of the SDK you're using doesn't support the project's target framework), prevented NuGet from creating the project assets file.</span></span> <span data-ttu-id="e3d5a-117">若要解決 NETSDK1004 錯誤，請解決先前的錯誤，然後 `dotnet restore` 在專案上執行。</span><span class="sxs-lookup"><span data-stu-id="e3d5a-117">To resolve the NETSDK1004 error, resolve the earlier error, and then run `dotnet restore` on the project.</span></span>
* <span data-ttu-id="e3d5a-118">App Center CI 正在建立一個專案，而該專案具有不在 NuGet 中的外部元件。</span><span class="sxs-lookup"><span data-stu-id="e3d5a-118">App Center CI is building a project that has an external assembly that is not in NuGet.</span></span> <span data-ttu-id="e3d5a-119">若要解決此錯誤，請使用元件的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="e3d5a-119">To resolve the error, use a NuGet package for the assembly.</span></span>

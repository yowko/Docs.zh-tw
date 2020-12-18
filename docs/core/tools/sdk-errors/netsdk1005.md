---
title: NETSDK1005 和 NETSDK1047：資產檔案遺失目標
description: 如何解決資產檔案遺失目標的問題。
author: sfoslund
ms.topic: error-reference
ms.date: 12/17/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: e3e7389adf6a9a715d44661a5f7cbae5efe299e4
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678163"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a><span data-ttu-id="ad1ad-103">NETSDK1005 和 NETSDK1047：資產檔案遺失目標</span><span class="sxs-lookup"><span data-stu-id="ad1ad-103">NETSDK1005 and NETSDK1047: Asset file is missing target</span></span>

<span data-ttu-id="ad1ad-104">本文 **適用于：** ✔️ .net CORE 2.1.100 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="ad1ad-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="ad1ad-105">當 .NET SDK 發出錯誤 NETSDK1005 或 NETSDK1047 時，專案的資產檔案就會遺失其中一個目標 framework 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ad1ad-105">When the .NET SDK issues error NETSDK1005 or NETSDK1047, the project's assets file is missing information on one of your target frameworks.</span></span> <span data-ttu-id="ad1ad-106">NuGet 會在 *obj* 資料夾中，將名為 *project.assets.js* 的檔案寫入，而 .net SDK 會使用它來取得封裝的相關資訊，以傳遞至編譯器。</span><span class="sxs-lookup"><span data-stu-id="ad1ad-106">NuGet writes a file named *project.assets.json* in the *obj* folder, and the .NET SDK uses it to get information about packages to pass into the compiler.</span></span> <span data-ttu-id="ad1ad-107">在 .NET 5 中，NuGet 新增了一個名為的新欄位 `TargetFrameworkAlias` ，因此較早版本的 MSBuild 或 NuGet 會產生資產檔案，而不會有新的欄位。</span><span class="sxs-lookup"><span data-stu-id="ad1ad-107">In .NET 5, NuGet added a new field named `TargetFrameworkAlias`, so earlier versions of MSBuild or NuGet generate an assets file without the new field.</span></span> <span data-ttu-id="ad1ad-108">如需詳細資訊，請參閱 [錯誤 NETSDK1005](https://developercommunity.visualstudio.com/content/problem/1248649/error-netsdk1005-assets-file-projectassetsjson-doe.html)。</span><span class="sxs-lookup"><span data-stu-id="ad1ad-108">For more information, see [error NETSDK1005](https://developercommunity.visualstudio.com/content/problem/1248649/error-netsdk1005-assets-file-projectassetsjson-doe.html).</span></span>

<span data-ttu-id="ad1ad-109">以下是您可以採取的一些動作，可以解決此錯誤：</span><span class="sxs-lookup"><span data-stu-id="ad1ad-109">Here are some actions you can take that may resolve the error:</span></span>

* <span data-ttu-id="ad1ad-110">請確定您使用的是 MSBuild 16.8 版或更新版本，以及 NuGet 5.8 版或更新版本，並在更新工具之後還原專案。</span><span class="sxs-lookup"><span data-stu-id="ad1ad-110">Make sure that you're using MSBuild version 16.8 or later and NuGet version 5.8 or later, and restore the project after updating your tools.</span></span> <span data-ttu-id="ad1ad-111">當您使用 NuGet 5.8 版或更新版本時，您應該使用 Visual Studio 2019 16.8 版或更新版本、MSBuild 16.8 版或更新版本，以及 .NET 5.0 SDK 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="ad1ad-111">When you're using NuGet version 5.8 or later, you should be using Visual Studio 2019 version 16.8 or later, MSBuild version 16.8 or later, and .NET 5.0 SDK or later.</span></span>

* <span data-ttu-id="ad1ad-112">如果您在安裝16.8 版之後，第一次在 Visual Studio 2019 中建立專案時收到錯誤，或是在變更專案的目標架構之後，請再次建立專案。</span><span class="sxs-lookup"><span data-stu-id="ad1ad-112">If you get the error while building a project in Visual Studio 2019 for the first time after installing version 16.8 or after changing the project's target framework, build the project a second time.</span></span>

* <span data-ttu-id="ad1ad-113">建立專案之前，請先刪除 *obj* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ad1ad-113">Delete the *obj* folder before building the project.</span></span>

* <span data-ttu-id="ad1ad-114">請確定專案的屬性中包含遺漏的目標值 `TargetFrameworks` 。</span><span class="sxs-lookup"><span data-stu-id="ad1ad-114">Make sure that the missing target value is included in the `TargetFrameworks` property of your project.</span></span>

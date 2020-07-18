---
title: '.NET Framework 4.8、4.7、4.6 和 4.5 移轉手冊 '
description: 遷移至新版 .NET Framework 版本的指南，其中包含新功能和應用程式相容性的資源。
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: a5b632824efacdb5e99228727b8751dc7f17d363
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "86443412"
---
# <a name="migrate-to-net-framework-48-47-46-and-45"></a><span data-ttu-id="1e9cb-103">遷移至 .NET Framework 4.8、4.7、4.6 和4。5</span><span class="sxs-lookup"><span data-stu-id="1e9cb-103">Migrate to .NET Framework 4.8, 4.7, 4.6, and 4.5</span></span>

<span data-ttu-id="1e9cb-104">如果您使用舊版的 .NET Framework 來建立應用程式，通常可以將它升級至 .NET Framework 4.5 及其點發行版（4.5.1 和4.5.2）、.NET Framework 4.6 及其點發行版（4.6.1 和4.6.2）、.NET Framework 4.7 及其單點發行版（4.7.1 和4.7.2），或輕鬆 .NET Framework 4.8。</span><span class="sxs-lookup"><span data-stu-id="1e9cb-104">If you created your app using an earlier version of .NET Framework, you can generally upgrade it to .NET Framework 4.5 and its point releases (4.5.1 and 4.5.2), .NET Framework 4.6 and its point releases (4.6.1 and 4.6.2), .NET Framework 4.7 and its point releases (4.7.1 and 4.7.2), or .NET Framework 4.8 easily.</span></span> <span data-ttu-id="1e9cb-105">在 Visual Studio 中，開啟您的專案。</span><span class="sxs-lookup"><span data-stu-id="1e9cb-105">Open your project in Visual Studio.</span></span> <span data-ttu-id="1e9cb-106">如果您的專案是使用舊版 Visual Studio 所建立，則會自動開啟 [專案相容性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1e9cb-106">If your project was created in an earlier version of Visual Studio, the **Project Compatibility** dialog box automatically opens.</span></span> <span data-ttu-id="1e9cb-107">如需升級 Visual Studio 專案的詳細資訊，請參閱[移植、移轉及升級 Visual Studio 專案](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)和 [Visual Studio 2019 平台目標及相容性](/visualstudio/releases/2019/compatibility)。</span><span class="sxs-lookup"><span data-stu-id="1e9cb-107">For more information about upgrading a project in Visual Studio, see [Port, Migrate, and Upgrade Visual Studio Projects](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) and [Visual Studio 2019 Platform Targeting and Compatibility](/visualstudio/releases/2019/compatibility).</span></span>

 <span data-ttu-id="1e9cb-108">不過，.NET Framework 中的某些變更需要變更您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1e9cb-108">However, some changes in .NET Framework require changes to your code.</span></span> <span data-ttu-id="1e9cb-109">您也可能想要利用 .NET Framework 4.5 及其小數點版本、.NET Framework 4.6 及其小數點版本、.NET Framework 4.7 及其小數點版本或 .NET Framework 4.8 中的某些新功能。</span><span class="sxs-lookup"><span data-stu-id="1e9cb-109">You may also want to take advantage of functionality that is new in .NET Framework 4.5 and its point releases, in .NET Framework 4.6 and its point releases, in .NET Framework 4.7 and its point releases, or in .NET Framework 4.8.</span></span> <span data-ttu-id="1e9cb-110">針對新版本的 .NET Framework，對應用程式進行這些類型的變更，通常稱為「*遷移*」。</span><span class="sxs-lookup"><span data-stu-id="1e9cb-110">Making these types of changes to your app for a new version of .NET Framework is typically referred to as *migration*.</span></span> <span data-ttu-id="1e9cb-111">如果您的應用程式不需要遷移，您可以在 .NET Framework 4.5 或更新版本中執行，而不需要重新編譯。</span><span class="sxs-lookup"><span data-stu-id="1e9cb-111">If your app doesn't have to be migrated, you can run it in .NET Framework 4.5 or a later version without recompiling it.</span></span>

## <a name="migration-resources"></a><span data-ttu-id="1e9cb-112">移轉資源</span><span class="sxs-lookup"><span data-stu-id="1e9cb-112">Migration resources</span></span>

<span data-ttu-id="1e9cb-113">將您的應用程式從舊版 .NET Framework 遷移至4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 或4.8 版本之前，請先參閱下列檔：</span><span class="sxs-lookup"><span data-stu-id="1e9cb-113">Review the following documents before you migrate your app from earlier versions of .NET Framework to version 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2, or 4.8:</span></span>

- <span data-ttu-id="1e9cb-114">請參閱[版本和相依性](versions-and-dependencies.md)，了解每個 .NET Framework 版本的基礎 CLR 版本，並檢閱成功設定應用程式目標的方針。</span><span class="sxs-lookup"><span data-stu-id="1e9cb-114">See [Versions and Dependencies](versions-and-dependencies.md) to understand the CLR version underlying each version of the .NET Framework and to review guidelines for targeting your apps successfully.</span></span>

- <span data-ttu-id="1e9cb-115">請參閱[應用程式相容性](application-compatibility.md)，瞭解可能影響應用程式的執行時間和重定變更，以及如何處理它們。</span><span class="sxs-lookup"><span data-stu-id="1e9cb-115">Review [Application compatibility](application-compatibility.md) to find out about runtime and retargeting changes that might affect your app and how to handle them.</span></span>

- <span data-ttu-id="1e9cb-116">檢閱[類別庫中已淘汰的功能](../whats-new/whats-obsolete.md)，以判斷您的程式碼中可能已淘汰的任何類型或成員，以及建議的替代做法。</span><span class="sxs-lookup"><span data-stu-id="1e9cb-116">Review [What's Obsolete in the Class Library](../whats-new/whats-obsolete.md) to determine any types or members in your code that have been made obsolete, and the recommended alternatives.</span></span>

- <span data-ttu-id="1e9cb-117">如需想要新增至應用程式之新功能的描述，請參閱[新功能](../whats-new/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1e9cb-117">See [What's New](../whats-new/index.md) for descriptions of new features that you may want to add to your app.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e9cb-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="1e9cb-118">See also</span></span>

- [<span data-ttu-id="1e9cb-119">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="1e9cb-119">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="1e9cb-120">從 .NET Framework 1.1 移轉</span><span class="sxs-lookup"><span data-stu-id="1e9cb-120">Migrating from the .NET Framework 1.1</span></span>](migrating-from-the-net-framework-1-1.md)
- [<span data-ttu-id="1e9cb-121">版本相容性</span><span class="sxs-lookup"><span data-stu-id="1e9cb-121">Version Compatibility</span></span>](version-compatibility.md)
- [<span data-ttu-id="1e9cb-122">版本和相依性</span><span class="sxs-lookup"><span data-stu-id="1e9cb-122">Versions and Dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="1e9cb-123">如何：將應用程式設定為支援 .NET Framework 4 或更新版本</span><span class="sxs-lookup"><span data-stu-id="1e9cb-123">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [<span data-ttu-id="1e9cb-124">新功能</span><span class="sxs-lookup"><span data-stu-id="1e9cb-124">What's New</span></span>](../whats-new/index.md)
- [<span data-ttu-id="1e9cb-125">類別庫中的過時功能</span><span class="sxs-lookup"><span data-stu-id="1e9cb-125">What's Obsolete in the Class Library</span></span>](../whats-new/whats-obsolete.md)
- [<span data-ttu-id="1e9cb-126">.NET Framework 官方支援原則</span><span class="sxs-lookup"><span data-stu-id="1e9cb-126">.NET Framework official support policy</span></span>](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [<span data-ttu-id="1e9cb-127">.NET Framework 4 移轉問題</span><span class="sxs-lookup"><span data-stu-id="1e9cb-127">.NET Framework 4 migration issues</span></span>](net-framework-4-migration-issues.md)

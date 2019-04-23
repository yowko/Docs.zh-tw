---
title: '.NET Framework 4.8、4.7、4.6 和 4.5 移轉手冊 '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb51a0be57992d65a88e958d76a5e371dc028a00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871445"
---
# <a name="migration-guide-to-the-net-framework-48-47-46-and-45"></a><span data-ttu-id="d68ee-102">.NET Framework 4.8、4.7、4.6 和 4.5 移轉手冊</span><span class="sxs-lookup"><span data-stu-id="d68ee-102">Migration Guide to the .NET Framework 4.8, 4.7, 4.6, and 4.5</span></span>

<span data-ttu-id="d68ee-103">如果您使用舊版的 .NET Framework 建立應用程式，通常可以輕鬆地將它升級到 .NET Framework 4.5 及其小數點版本 (4.5.1 和 4.5.2)、.NET Framework 4.6 及其小數點版本 (4.6.1 和 4.6.2)、.NET Framework 4.7 及其小數點版本 (4.7.1 和 4.7.2) 或 .NET Framework 4.8。</span><span class="sxs-lookup"><span data-stu-id="d68ee-103">If you created your app using an earlier version of the .NET Framework, you can generally upgrade it to .NET Framework 4.5 and its point releases (4.5.1 and 4.5.2), .NET Framework 4.6 and its point releases (4.6.1 and 4.6.2), .NET Framework 4.7 and its point releases (4.7.1 and 4.7.2), or .NET Framework 4.8 easily.</span></span> <span data-ttu-id="d68ee-104">在 Visual Studio 中開啟專案。</span><span class="sxs-lookup"><span data-stu-id="d68ee-104">Open your project in Visual Studio.</span></span> <span data-ttu-id="d68ee-105">如果您的專案是使用舊版 Visual Studio 所建立，則會自動開啟 [專案相容性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d68ee-105">If your project was created in an earlier version of Visual Studio, the **Project Compatibility** dialog box automatically opens.</span></span> <span data-ttu-id="d68ee-106">如需升級 Visual Studio 專案的詳細資訊，請參閱[移植、移轉及升級 Visual Studio 專案](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)和 [Visual Studio 2019 平台目標及相容性](/visualstudio/releases/2019/compatibility)。</span><span class="sxs-lookup"><span data-stu-id="d68ee-106">For more information about upgrading a project in Visual Studio, see [Port, Migrate, and Upgrade Visual Studio Projects](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) and [Visual Studio 2019 Platform Targeting and Compatibility](/visualstudio/releases/2019/compatibility).</span></span>

 <span data-ttu-id="d68ee-107">不過，.NET Framework 中的某些變更需要變更您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d68ee-107">However, some changes in the .NET Framework require changes to your code.</span></span> <span data-ttu-id="d68ee-108">您也可能想要利用 .NET Framework 4.5 及其小數點版本、.NET Framework 4.6 及其小數點版本、.NET Framework 4.7 及其小數點版本或 .NET Framework 4.8 中的某些新功能。</span><span class="sxs-lookup"><span data-stu-id="d68ee-108">You may also want to take advantage of functionality that is new in .NET Framework 4.5 and its point releases, in .NET Framework 4.6 and its point releases, in .NET Framework 4.7 and its point releases, or in .NET Framework 4.8.</span></span> <span data-ttu-id="d68ee-109">針對新版 .NET Framework 對您應用程式所做之這些類型的變更通常稱為「移轉」。</span><span class="sxs-lookup"><span data-stu-id="d68ee-109">Making these types of changes to your app for a new version of the .NET Framework is typically referred to as *migration*.</span></span> <span data-ttu-id="d68ee-110">如果您的應用程式不必移轉，您可以在 .NET Framework 4.5 或更新版本中執行它，而不需要重新編譯。</span><span class="sxs-lookup"><span data-stu-id="d68ee-110">If your app doesn't have to be migrated, you can run it in the .NET Framework 4.5 or a later version without recompiling it.</span></span>

## <a name="migration-resources"></a><span data-ttu-id="d68ee-111">移轉資源</span><span class="sxs-lookup"><span data-stu-id="d68ee-111">Migration resources</span></span>

<span data-ttu-id="d68ee-112">將您的應用程式從舊版 .NET Framework 移轉至 4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1 或 4.7.2 或 4.8 之前，請先檢閱下列文件：</span><span class="sxs-lookup"><span data-stu-id="d68ee-112">Review the following documents before you migrate your app from earlier versions of the .NET Framework to version 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2, or 4.8:</span></span>

- <span data-ttu-id="d68ee-113">請參閱[版本和相依性](versions-and-dependencies.md)，了解每個 .NET Framework 版本的基礎 CLR 版本，並檢閱成功設定應用程式目標的方針。</span><span class="sxs-lookup"><span data-stu-id="d68ee-113">See [Versions and Dependencies](versions-and-dependencies.md) to understand the CLR version underlying each version of the .NET Framework and to review guidelines for targeting your apps successfully.</span></span>

- <span data-ttu-id="d68ee-114">檢閱[應用程式相容性](application-compatibility.md)，了解可能影響應用程式的執行階段和重定目標變更，以及如何處理這些變更。</span><span class="sxs-lookup"><span data-stu-id="d68ee-114">Review [Application Compatibility](application-compatibility.md) to find out about runtime and retargeting changes that might affect your app and how to handle them.</span></span>

- <span data-ttu-id="d68ee-115">檢閱[類別庫中已淘汰的功能](../whats-new/whats-obsolete.md)，以判斷您的程式碼中可能已淘汰的任何類型或成員，以及建議的替代做法。</span><span class="sxs-lookup"><span data-stu-id="d68ee-115">Review [What's Obsolete in the Class Library](../whats-new/whats-obsolete.md) to determine any types or members in your code that have been made obsolete, and the recommended alternatives.</span></span>

- <span data-ttu-id="d68ee-116">如需想要新增至應用程式之新功能的描述，請參閱[新功能](../whats-new/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d68ee-116">See [What's New](../whats-new/index.md) for descriptions of new features that you may want to add to your app.</span></span>

## <a name="see-also"></a><span data-ttu-id="d68ee-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d68ee-117">See also</span></span>

- [<span data-ttu-id="d68ee-118">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="d68ee-118">Application Compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="d68ee-119">從 .NET Framework 1.1 移轉</span><span class="sxs-lookup"><span data-stu-id="d68ee-119">Migrating from the .NET Framework 1.1</span></span>](migrating-from-the-net-framework-1-1.md)
- [<span data-ttu-id="d68ee-120">版本相容性</span><span class="sxs-lookup"><span data-stu-id="d68ee-120">Version Compatibility</span></span>](version-compatibility.md)
- [<span data-ttu-id="d68ee-121">版本和相依性</span><span class="sxs-lookup"><span data-stu-id="d68ee-121">Versions and Dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="d68ee-122">如何：設定應用程式以支援 .NET Framework 4 或更新版本</span><span class="sxs-lookup"><span data-stu-id="d68ee-122">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [<span data-ttu-id="d68ee-123">新功能</span><span class="sxs-lookup"><span data-stu-id="d68ee-123">What's New</span></span>](../whats-new/index.md)
- [<span data-ttu-id="d68ee-124">類別庫中已淘汰的功能</span><span class="sxs-lookup"><span data-stu-id="d68ee-124">What's Obsolete in the Class Library</span></span>](../whats-new/whats-obsolete.md)
- [<span data-ttu-id="d68ee-125">.NET Framework 版本和組件資訊</span><span class="sxs-lookup"><span data-stu-id="d68ee-125">.NET Framework Version and Assembly Information</span></span>](https://go.microsoft.com/fwlink/?LinkId=201701)
- [<span data-ttu-id="d68ee-126">Microsoft .NET Framework 支援週期原則</span><span class="sxs-lookup"><span data-stu-id="d68ee-126">Microsoft .NET Framework Support Lifecycle Policy</span></span>](https://go.microsoft.com/fwlink/?LinkId=196607)
- [<span data-ttu-id="d68ee-127">.NET Framework 4 移轉問題</span><span class="sxs-lookup"><span data-stu-id="d68ee-127">.NET Framework 4 migration issues</span></span>](net-framework-4-migration-issues.md)
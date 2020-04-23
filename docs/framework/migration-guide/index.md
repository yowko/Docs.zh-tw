---
title: '.NET Framework 4.8、4.7、4.6 和 4.5 移轉手冊 '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: fbaee646f7adcfe1a53d4231790e4258fd95a892
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102628"
---
# <a name="migrate-to-net-framework-48-47-46-and-45"></a><span data-ttu-id="16d1d-102">移至 .NET 框架 4.8、4.7、4.6 和 4.5</span><span class="sxs-lookup"><span data-stu-id="16d1d-102">Migrate to .NET Framework 4.8, 4.7, 4.6, and 4.5</span></span>

<span data-ttu-id="16d1d-103">如果使用早期版本的 .NET Framework 創建應用,通常可以將其升級到 .NET Framework 4.5 及其點版本(4.5.1 和 4.5.2)、.NET Framework 4.6 及其點版本(4.6.1 和 4.6.2)、.NET Framework 4.7 及其點版本(4.7.1 和 4.7.2)或 .NET Framework 4.8。</span><span class="sxs-lookup"><span data-stu-id="16d1d-103">If you created your app using an earlier version of .NET Framework, you can generally upgrade it to .NET Framework 4.5 and its point releases (4.5.1 and 4.5.2), .NET Framework 4.6 and its point releases (4.6.1 and 4.6.2), .NET Framework 4.7 and its point releases (4.7.1 and 4.7.2), or .NET Framework 4.8 easily.</span></span> <span data-ttu-id="16d1d-104">在 Visual Studio 中，開啟您的專案。</span><span class="sxs-lookup"><span data-stu-id="16d1d-104">Open your project in Visual Studio.</span></span> <span data-ttu-id="16d1d-105">如果您的專案是使用舊版 Visual Studio 所建立，則會自動開啟 [專案相容性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="16d1d-105">If your project was created in an earlier version of Visual Studio, the **Project Compatibility** dialog box automatically opens.</span></span> <span data-ttu-id="16d1d-106">如需升級 Visual Studio 專案的詳細資訊，請參閱[移植、移轉及升級 Visual Studio 專案](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)和 [Visual Studio 2019 平台目標及相容性](/visualstudio/releases/2019/compatibility)。</span><span class="sxs-lookup"><span data-stu-id="16d1d-106">For more information about upgrading a project in Visual Studio, see [Port, Migrate, and Upgrade Visual Studio Projects](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) and [Visual Studio 2019 Platform Targeting and Compatibility](/visualstudio/releases/2019/compatibility).</span></span>

 <span data-ttu-id="16d1d-107">但是,.NET 框架中的一些更改需要更改代碼。</span><span class="sxs-lookup"><span data-stu-id="16d1d-107">However, some changes in .NET Framework require changes to your code.</span></span> <span data-ttu-id="16d1d-108">您也可能想要利用 .NET Framework 4.5 及其小數點版本、.NET Framework 4.6 及其小數點版本、.NET Framework 4.7 及其小數點版本或 .NET Framework 4.8 中的某些新功能。</span><span class="sxs-lookup"><span data-stu-id="16d1d-108">You may also want to take advantage of functionality that is new in .NET Framework 4.5 and its point releases, in .NET Framework 4.6 and its point releases, in .NET Framework 4.7 and its point releases, or in .NET Framework 4.8.</span></span> <span data-ttu-id="16d1d-109">新增版本 .NET Framework 的應用程式進行這些類型的變更通常為*移轉*。</span><span class="sxs-lookup"><span data-stu-id="16d1d-109">Making these types of changes to your app for a new version of .NET Framework is typically referred to as *migration*.</span></span> <span data-ttu-id="16d1d-110">如果應用不必遷移,則可以在 .NET Framework 4.5 或更高版本中運行它,而無需重新編譯它。</span><span class="sxs-lookup"><span data-stu-id="16d1d-110">If your app doesn't have to be migrated, you can run it in .NET Framework 4.5 or a later version without recompiling it.</span></span>

## <a name="migration-resources"></a><span data-ttu-id="16d1d-111">移轉資源</span><span class="sxs-lookup"><span data-stu-id="16d1d-111">Migration resources</span></span>

<span data-ttu-id="16d1d-112">將應用從早期版本的 .NET Framework 遷移到版本 4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.6.2、4.7、4.7.1、4.7.2 或 4.8 之前,請查看以下文檔:</span><span class="sxs-lookup"><span data-stu-id="16d1d-112">Review the following documents before you migrate your app from earlier versions of .NET Framework to version 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2, or 4.8:</span></span>

- <span data-ttu-id="16d1d-113">請參閱[版本和相依性](versions-and-dependencies.md)，了解每個 .NET Framework 版本的基礎 CLR 版本，並檢閱成功設定應用程式目標的方針。</span><span class="sxs-lookup"><span data-stu-id="16d1d-113">See [Versions and Dependencies](versions-and-dependencies.md) to understand the CLR version underlying each version of the .NET Framework and to review guidelines for targeting your apps successfully.</span></span>

- <span data-ttu-id="16d1d-114">查看[應用程式相容性](application-compatibility.md),瞭解可能影響應用的運行時更改和重新定位更改以及如何處理這些更改。</span><span class="sxs-lookup"><span data-stu-id="16d1d-114">Review [Application compatibility](application-compatibility.md) to find out about runtime and retargeting changes that might affect your app and how to handle them.</span></span>

- <span data-ttu-id="16d1d-115">檢閱[類別庫中已淘汰的功能](../whats-new/whats-obsolete.md)，以判斷您的程式碼中可能已淘汰的任何類型或成員，以及建議的替代做法。</span><span class="sxs-lookup"><span data-stu-id="16d1d-115">Review [What's Obsolete in the Class Library](../whats-new/whats-obsolete.md) to determine any types or members in your code that have been made obsolete, and the recommended alternatives.</span></span>

- <span data-ttu-id="16d1d-116">如需想要新增至應用程式之新功能的描述，請參閱[新功能](../whats-new/index.md)。</span><span class="sxs-lookup"><span data-stu-id="16d1d-116">See [What's New](../whats-new/index.md) for descriptions of new features that you may want to add to your app.</span></span>

## <a name="see-also"></a><span data-ttu-id="16d1d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16d1d-117">See also</span></span>

- [<span data-ttu-id="16d1d-118">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="16d1d-118">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="16d1d-119">從 .NET Framework 1.1 移轉</span><span class="sxs-lookup"><span data-stu-id="16d1d-119">Migrating from the .NET Framework 1.1</span></span>](migrating-from-the-net-framework-1-1.md)
- [<span data-ttu-id="16d1d-120">版本相容性</span><span class="sxs-lookup"><span data-stu-id="16d1d-120">Version Compatibility</span></span>](version-compatibility.md)
- [<span data-ttu-id="16d1d-121">版本和相依項</span><span class="sxs-lookup"><span data-stu-id="16d1d-121">Versions and Dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="16d1d-122">如何:將應用設定為支援 .NET 框架 4 或更高版本</span><span class="sxs-lookup"><span data-stu-id="16d1d-122">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [<span data-ttu-id="16d1d-123">新功能</span><span class="sxs-lookup"><span data-stu-id="16d1d-123">What's New</span></span>](../whats-new/index.md)
- [<span data-ttu-id="16d1d-124">類別庫中的過時功能</span><span class="sxs-lookup"><span data-stu-id="16d1d-124">What's Obsolete in the Class Library</span></span>](../whats-new/whats-obsolete.md)
- [<span data-ttu-id="16d1d-125">.NET 框架官方支援政策</span><span class="sxs-lookup"><span data-stu-id="16d1d-125">.NET Framework official support policy</span></span>](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [<span data-ttu-id="16d1d-126">.NET Framework 4 移轉問題</span><span class="sxs-lookup"><span data-stu-id="16d1d-126">.NET Framework 4 migration issues</span></span>](net-framework-4-migration-issues.md)

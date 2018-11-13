---
title: 發行 NuGet 套件
description: 發行 .NET 程式庫到 NuGet 的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: e0244d2a9d09382c289c74a45969bca0a1311445
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "50757305"
---
# <a name="publishing-a-nuget-package"></a><span data-ttu-id="8b8a4-103">發行 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="8b8a4-103">Publishing a NuGet package</span></span>

<span data-ttu-id="8b8a4-104">NuGet 套件發行之後可從套件存放庫取用。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-104">NuGet packages are published and consumed from package repositories.</span></span> <span data-ttu-id="8b8a4-105">雖然 NuGet.org 是最廣為人知且最常被使用的存放庫，還有許多其他可以發佈 NuGet 套件的地方：</span><span class="sxs-lookup"><span data-stu-id="8b8a4-105">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages:</span></span>

* <span data-ttu-id="8b8a4-106">**[NuGet.org](https://www.nuget.org/)** 是 NuGet 套件的主要線上存放庫。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-106">**[NuGet.org](https://www.nuget.org/)** is the primary online repository for NuGet packages.</span></span> <span data-ttu-id="8b8a4-107">NuGet.org 上的所有套件都可供大眾使用。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-107">All packages on NuGet.org are publicly available to everyone.</span></span> <span data-ttu-id="8b8a4-108">根據預設，Visual Studio 使用 NuGet.org 做為套件來源，而且對許多開發人員而言，NuGet.org 是他們與其互動的唯一套件存放庫。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-108">By default, Visual Studio has NuGet.org as a package source and for many developers NuGet.org is the only package repository they'll interact with.</span></span> <span data-ttu-id="8b8a4-109">NuGet.org 是發行穩定套件與您想要從社群取得意見反應之發行前版本套件的最佳位置。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-109">NuGet.org is the best place to publish stable packages and pre-release packages that you want community feedback on.</span></span>

* <span data-ttu-id="8b8a4-110">**[MyGet](https://myget.org/)** 是一個存放庫服務，它支援為開放原始碼專案自訂套件摘要。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-110">**[MyGet](https://myget.org/)** is a repository service that supports custom package feeds for open-source projects.</span></span> <span data-ttu-id="8b8a4-111">MyGet 公用自訂摘要是發行由您的 CI 服務建立之發行前版本套件的理想位置。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-111">A MyGet public custom feed is an ideal place to publish pre-release packages created by your CI service.</span></span> <span data-ttu-id="8b8a4-112">MyGet 也提供商業用私人摘要。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-112">MyGet also provides private feeds commercially.</span></span>

* <span data-ttu-id="8b8a4-113">**[本機摘要](/nuget/hosting-packages/local-feeds)** 可讓您將資料夾視為套件存放庫，並讓該資料夾中的 `*.nupkg` 檔案可由 NuGet 存取。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-113">A **[local feed](/nuget/hosting-packages/local-feeds)** allows you to treat a folder like a package repository and makes the `*.nupkg` files in the folder accessible by NuGet.</span></span> <span data-ttu-id="8b8a4-114">在將 NuGet 套件發行到 NuGet.org 之前進行測試時，本機摘要很實用。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-114">A local feed is useful for testing a NuGet package before publishing it to NuGet.org.</span></span>

> [!NOTE]
> <span data-ttu-id="8b8a4-115">一旦套件上傳，NuGet.org 便[不允許刪除套件](/nuget/policies/deleting-packages)。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-115">NuGet.org [does not allow a package to be deleted](/nuget/policies/deleting-packages) once it is uploaded.</span></span> <span data-ttu-id="8b8a4-116">您可以將套件取消列出，這樣它在 UI 中就不會被大眾看見，但還原時仍能下載 `*.nupkg`。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-116">A package can be unlisted so that it is not publicly visible in the UI but the `*.nupkg` can still be downloaded on restore.</span></span> <span data-ttu-id="8b8a4-117">此外，nuget.org 也不允許重複的套件版本。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-117">Also, nuget.org does not allow duplicate package versions.</span></span> <span data-ttu-id="8b8a4-118">若要修正發生錯誤的 NuGet 套件，您必須取消列出不正確的套件、累加版本號碼，然後發行新版本的套件。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-118">To correct a NuGet package with an error you have to unlist the incorrect package, increment the version number and publish a new version of the package.</span></span>

<span data-ttu-id="8b8a4-119">**✔️ 請務必**[發行穩定套件與您想要從社群取得意見反應之發行前版本套件](/nuget/create-packages/publish-a-package) 到 NuGet.org。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-119">**✔️ DO** [publish stable packages and pre-release packages](/nuget/create-packages/publish-a-package) you want community feedback on to NuGet.org.</span></span>

<span data-ttu-id="8b8a4-120">**✔️ 考慮**從持續整合組建將發行前版本套件發行到 MyGet 摘要。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-120">**✔️ CONSIDER** publishing pre-release packages to a MyGet feed from a continuous integration build.</span></span>

<span data-ttu-id="8b8a4-121">**✔️ 考慮**使用本機摘要或 MyGet 在您的開發環境測試套件。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-121">**✔️ CONSIDER** testing packages in your development environment using a local feed or MyGet.</span></span> <span data-ttu-id="8b8a4-122">檢查套件是否正常運作並將它發行到 NuGet.org。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-122">Check the package works then publish it to NuGet.org.</span></span>

## <a name="nugetorg-security"></a><span data-ttu-id="8b8a4-123">NuGet.org 安全性</span><span class="sxs-lookup"><span data-stu-id="8b8a4-123">NuGet.org security</span></span>

<span data-ttu-id="8b8a4-124">請務必透過適當機制保護您的 NuGet 帳戶，避免惡意使用者上傳您程式庫的惡意版本。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-124">It's important that bad actors can't access your NuGet account and upload a malicious version of your library.</span></span> <span data-ttu-id="8b8a4-125">NuGet.org 提供套件發行時的雙因素驗證與電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-125">NuGet.org offers two-factor authentication and email notifications when a package is published.</span></span> <span data-ttu-id="8b8a4-126">登入 NuGet.org 之後在 [帳戶設定] 頁面上啟用這些功能。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-126">Enable these features after logging into NuGet.org on the **Account settings** page.</span></span>

<span data-ttu-id="8b8a4-127">![替代文字](./media/publish-nuget-package/nuget-2fa.png "NuGet 帳戶安全性")</span><span class="sxs-lookup"><span data-stu-id="8b8a4-127">![alt text](./media/publish-nuget-package/nuget-2fa.png "NuGet Account Security")</span></span>

<span data-ttu-id="8b8a4-128">**✔️ 請務必**使用 Microsoft 帳戶來登入 NuGet。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-128">**✔️ DO** use a Microsoft account to sign in to NuGet.</span></span>

<span data-ttu-id="8b8a4-129">**✔️ 請務必** 針對存取 NuGet 啟用雙因素驗證。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-129">**✔️ DO** enable two-factor authentication for accessing NuGet.</span></span>

<span data-ttu-id="8b8a4-130">**✔️ 請務必**啟用套件發行時的電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="8b8a4-130">**✔️ DO** enable email notification when a package is published.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="8b8a4-131">[上一頁](./sourcelink.md)
[下一頁](./versioning.md)</span><span class="sxs-lookup"><span data-stu-id="8b8a4-131">[Previous](./sourcelink.md)
[Next](./versioning.md)</span></span>

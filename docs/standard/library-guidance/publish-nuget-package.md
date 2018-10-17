---
title: 發行 NuGet 套件
description: 發佈至 NuGet 的.NET 程式庫的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 0602712311411ef3d59825bec8c5e550bc8d8265
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2018
ms.locfileid: "49369799"
---
# <a name="publishing-a-nuget-package"></a><span data-ttu-id="ea3fe-103">發行 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="ea3fe-103">Publishing a NuGet package</span></span>

<span data-ttu-id="ea3fe-104">NuGet 套件發行，且從套件存放庫取用。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-104">NuGet packages are published and consumed from package repositories.</span></span> <span data-ttu-id="ea3fe-105">雖然 NuGet.org 最廣泛是已知且使用的儲存機制，有許多地方，若要發佈 NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="ea3fe-105">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages:</span></span>

* <span data-ttu-id="ea3fe-106">**[NuGet.org](https://www.nuget.org/)** 是 NuGet 套件的主要線上存放庫。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-106">**[NuGet.org](https://www.nuget.org/)** is the primary online repository for NuGet packages.</span></span> <span data-ttu-id="ea3fe-107">公開提供給所有人在 NuGet.org 上的所有封裝都。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-107">All packages on NuGet.org are publicly available to everyone.</span></span> <span data-ttu-id="ea3fe-108">根據預設，Visual Studio NuGet.org 與套件來源，並且適用於許多開發人員 NuGet.org 是唯一的套件存放庫會與它們進行互動。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-108">By default, Visual Studio has NuGet.org as a package source and for many developers NuGet.org is the only package repository they'll interact with.</span></span> <span data-ttu-id="ea3fe-109">NuGet.org 是穩定的封裝和發行前版本封裝上想要的社群的意見反應所發行的最佳位置。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-109">NuGet.org is the best place to publish stable packages and pre-release packages that you want community feedback on.</span></span>

* <span data-ttu-id="ea3fe-110">**[MyGet](https://myget.org/)** 存放庫服務支援[開放原始碼專案的可用的自訂套件摘要](https://www.myget.org/opensource)。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-110">**[MyGet](https://myget.org/)** repository service supports [free custom package feeds for open-source projects](https://www.myget.org/opensource).</span></span> <span data-ttu-id="ea3fe-111">MyGet 公開自訂摘要是一個理想位置來發佈您的 CI 服務所建立的發行前版本套件。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-111">A MyGet public custom feed is an ideal place to publish pre-release packages created by your CI service.</span></span> <span data-ttu-id="ea3fe-112">MyGet 也私用摘要會盡一切商業上的提供。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-112">MyGet also provides private feeds commercially.</span></span>

* <span data-ttu-id="ea3fe-113">A **[本機摘要](/nuget/hosting-packages/local-feeds)** 可讓您將像是套件存放庫的資料夾，並使`*.nupkg`nuget 的可存取資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-113">A **[local feed](/nuget/hosting-packages/local-feeds)** allows you to treat a folder like a package repository and makes the `*.nupkg` files in the folder accessible by NuGet.</span></span> <span data-ttu-id="ea3fe-114">本機摘要可用於測試前將其發佈至 NuGet.org 的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-114">A local feed is useful for testing a NuGet package before publishing it to NuGet.org.</span></span>

> [!NOTE]
> <span data-ttu-id="ea3fe-115">NuGet.org[不允許刪除封裝](/nuget/policies/deleting-packages)一旦上傳。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-115">NuGet.org [does not allow a package to be deleted](/nuget/policies/deleting-packages) once it is uploaded.</span></span> <span data-ttu-id="ea3fe-116">封裝可以是未列出，以便公開在 UI 中看不到但`*.nupkg`仍可以下載 [還原]。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-116">A package can be unlisted so that it is not publicly visible in the UI but the `*.nupkg` can still be downloaded on restore.</span></span> <span data-ttu-id="ea3fe-117">此外，nuget.org 不允許重複的套件版本。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-117">Also, nuget.org does not allow duplicate package versions.</span></span> <span data-ttu-id="ea3fe-118">若要更正的錯誤，您必須取消列出不正確的套件的 NuGet 封裝，遞增版本號碼，並發行新版本的封裝。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-118">To correct a NuGet package with an error you have to unlist the incorrect package, increment the version number and publish a new version of the package.</span></span>

<span data-ttu-id="ea3fe-119">**✔️ 嗎**[發行穩定的封裝和發行前版本封裝](/nuget/create-packages/publish-a-package)想社群的意見反應到 NuGet.org。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-119">**✔️ DO** [publish stable packages and pre-release packages](/nuget/create-packages/publish-a-package) you want community feedback on to NuGet.org.</span></span>

<span data-ttu-id="ea3fe-120">**請考慮 ✔️**發行前版本套件發行至 MyGet 摘要，從持續整合組建。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-120">**✔️ CONSIDER** publishing pre-release packages to a MyGet feed from a continuous integration build.</span></span>

<span data-ttu-id="ea3fe-121">**請考慮 ✔️**使用本機摘要或 MyGet 開發環境中測試的封裝。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-121">**✔️ CONSIDER** testing packages in your development environment using a local feed or MyGet.</span></span> <span data-ttu-id="ea3fe-122">檢查封裝的運作方式，然後將它發行到 NuGet.org。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-122">Check the package works then publish it to NuGet.org.</span></span>

## <a name="nugetorg-security"></a><span data-ttu-id="ea3fe-123">NuGet.org 安全性</span><span class="sxs-lookup"><span data-stu-id="ea3fe-123">NuGet.org security</span></span>

<span data-ttu-id="ea3fe-124">很重要的不良執行者無法存取您的 NuGet 帳戶，並上傳您的程式庫的惡意版本。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-124">It's important that bad actors can't access your NuGet account and upload a malicious version of your library.</span></span> <span data-ttu-id="ea3fe-125">發佈封裝時，NuGet.org 會提供雙因素驗證和電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-125">NuGet.org offers two-factor authentication and email notifications when a package is published.</span></span> <span data-ttu-id="ea3fe-126">登入 NuGet.org 之後啟用這些功能，在**帳戶設定**頁面。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-126">Enable these features after logging into NuGet.org on the **Account settings** page.</span></span>

<span data-ttu-id="ea3fe-127">![替代文字](./media/publish-nuget-package/nuget-2fa.png "NuGet 帳戶安全性")</span><span class="sxs-lookup"><span data-stu-id="ea3fe-127">![alt text](./media/publish-nuget-package/nuget-2fa.png "NuGet Account Security")</span></span>

<span data-ttu-id="ea3fe-128">**請勿 ✔️**使用 Microsoft 帳戶登入 NuGet。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-128">**✔️ DO** use a Microsoft account to sign in to NuGet.</span></span>

<span data-ttu-id="ea3fe-129">**請勿 ✔️**啟用雙因素驗證，以存取 NuGet。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-129">**✔️ DO** enable two-factor authentication for accessing NuGet.</span></span>

<span data-ttu-id="ea3fe-130">**請勿 ✔️**發佈封裝時，啟用電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="ea3fe-130">**✔️ DO** enable email notification when a package is published.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="ea3fe-131">[上一頁](./sourcelink.md)
[下一頁](./versioning.md)</span><span class="sxs-lookup"><span data-stu-id="ea3fe-131">[Previous](./sourcelink.md)
[Next](./versioning.md)</span></span>

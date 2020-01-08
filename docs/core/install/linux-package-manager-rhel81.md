---
title: 在 Linux RHEL 8.1 套件管理員上安裝 .NET Core （.NET Core）
description: 使用套件管理員，在 RHEL 8.1 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 8674b5d9d0f0ee384ca6798a7ea699bad67c5e5e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341199"
---
# <a name="rhel-81-package-manager---install-net-core"></a><span data-ttu-id="b799f-103">RHEL 8.1 套件管理員-安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="b799f-103">RHEL 8.1 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="b799f-104">本文說明如何使用套件管理員在 RHEL 8.1 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="b799f-104">This article describes how to use a package manager to install .NET Core on RHEL 8.1.</span></span> <span data-ttu-id="b799f-105">RHEL 8.1 尚無法使用 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="b799f-105">.NET Core 3.1 is not yet available for RHEL 8.1.</span></span>

> [!NOTE]
> <span data-ttu-id="b799f-106">RHEL 8.0 不包含 .NET Core 3.0。</span><span class="sxs-lookup"><span data-stu-id="b799f-106">RHEL 8.0 does not include .NET Core 3.0.</span></span> <span data-ttu-id="b799f-107">使用命令 `yum upgrade` 來更新至 RHEL 8.1。</span><span class="sxs-lookup"><span data-stu-id="b799f-107">Use the command `yum upgrade` to update to RHEL 8.1.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="b799f-108">註冊您的 Red Hat 訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="b799f-108">Register your Red Hat subscription</span></span>

<span data-ttu-id="b799f-109">若要從 RHEL 上的 Red Hat 安裝 .NET Core，您必須先使用 Red Hat 訂用帳戶管理員進行註冊。</span><span class="sxs-lookup"><span data-stu-id="b799f-109">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="b799f-110">如果未在您的系統上完成此動作，或您不確定，請參閱[.Net Core 的 Red Hat 產品檔](https://access.redhat.com/documentation/net_core/)。</span><span class="sxs-lookup"><span data-stu-id="b799f-110">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="b799f-111">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="b799f-111">Install the .NET Core SDK</span></span>

<span data-ttu-id="b799f-112">向訂閱管理員註冊之後，您就可以開始安裝和啟用 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="b799f-112">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="b799f-113">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="b799f-113">In your terminal, run the following commands.</span></span>

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="b799f-114">安裝 ASP.NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="b799f-114">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="b799f-115">向訂閱管理員註冊之後，您就可以開始安裝和啟用 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="b799f-115">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="b799f-116">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="b799f-116">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="b799f-117">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="b799f-117">Install the .NET Core Runtime</span></span>

<span data-ttu-id="b799f-118">向訂用帳戶管理員註冊之後，您就可以開始安裝和啟用 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="b799f-118">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="b799f-119">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="b799f-119">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```

## <a name="see-also"></a><span data-ttu-id="b799f-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="b799f-120">See also</span></span>

- [<span data-ttu-id="b799f-121">在 Red Hat Enterprise Linux 8 上使用 .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b799f-121">Using .NET Core 3.0 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide_for_rhel_8/gs_install_dotnet)

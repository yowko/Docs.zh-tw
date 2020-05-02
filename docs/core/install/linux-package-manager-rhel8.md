---
title: 在 Linux RHEL 8 套件管理員上安裝 .NET Core-.NET Core
description: 使用套件管理員，在 RHEL 8 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 05/01/2020
ms.openlocfilehash: 8829e842e920e6abd4184b5140f80bb016acace2
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728233"
---
# <a name="rhel-8-package-manager---install-net-core"></a><span data-ttu-id="c5dfc-103">RHEL 8 套件管理員-安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="c5dfc-103">RHEL 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="c5dfc-104">本文說明如何使用套件管理員，在 Red Hat Enterprise Linux （RHEL）8上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="c5dfc-104">This article describes how to use a package manager to install .NET Core on Red Hat Enterprise Linux (RHEL) 8.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="c5dfc-105">註冊您的 Red Hat 訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="c5dfc-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="c5dfc-106">若要從 RHEL 上的 Red Hat 安裝 .NET Core，您必須先使用 Red Hat 訂用帳戶管理員進行註冊。</span><span class="sxs-lookup"><span data-stu-id="c5dfc-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="c5dfc-107">如果未在您的系統上完成此動作，或您不確定，請參閱[.Net Core 的 Red Hat 產品檔](https://access.redhat.com/documentation/net_core/)。</span><span class="sxs-lookup"><span data-stu-id="c5dfc-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="c5dfc-108">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c5dfc-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="c5dfc-109">向訂閱管理員註冊之後，您就可以開始安裝和啟用 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="c5dfc-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="c5dfc-110">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c5dfc-110">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="c5dfc-111">安裝 ASP.NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="c5dfc-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="c5dfc-112">向訂閱管理員註冊之後，您就可以開始安裝和啟用 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="c5dfc-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="c5dfc-113">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c5dfc-113">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="c5dfc-114">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="c5dfc-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="c5dfc-115">向訂用帳戶管理員註冊之後，您就可以開始安裝和啟用 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="c5dfc-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="c5dfc-116">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c5dfc-116">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="c5dfc-117">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="c5dfc-117">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="see-also"></a><span data-ttu-id="c5dfc-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5dfc-118">See also</span></span>

- [<span data-ttu-id="c5dfc-119">在 Red Hat Enterprise Linux 8 上使用 .NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="c5dfc-119">Using .NET Core 3.1 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)

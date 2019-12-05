---
title: 在 Linux RHEL 8.1 套件管理員上安裝 .NET Core （.NET Core）
description: 使用套件管理員，在 RHEL 8.1 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 20fb3e9e517858b9cc5d6e9c1bd97bf949558843
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800738"
---
# <a name="rhel-81-package-manager---install-net-core"></a><span data-ttu-id="64740-103">RHEL 8.1 套件管理員-安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="64740-103">RHEL 8.1 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="64740-104">本文說明如何使用套件管理員在 RHEL 8.1 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="64740-104">This article describes how to use a package manager to install .NET Core on RHEL 8.1.</span></span>

> [!NOTE]
> <span data-ttu-id="64740-105">RHEL 8.0 不包含 .NET Core 3.0。</span><span class="sxs-lookup"><span data-stu-id="64740-105">RHEL 8.0 does not include .NET Core 3.0.</span></span> <span data-ttu-id="64740-106">使用命令 `yum upgrade` 來更新至 RHEL 8.1。</span><span class="sxs-lookup"><span data-stu-id="64740-106">Use the command `yum upgrade` to update to RHEL 8.1.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="64740-107">註冊您的 Red Hat 訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="64740-107">Register your Red Hat subscription</span></span>

<span data-ttu-id="64740-108">若要從 RHEL 上的 Red Hat 安裝 .NET Core，您必須先使用 Red Hat 訂用帳戶管理員進行註冊。</span><span class="sxs-lookup"><span data-stu-id="64740-108">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="64740-109">如果未在您的系統上完成此動作，或您不確定，請參閱[.Net Core 的 Red Hat 產品檔](https://access.redhat.com/documentation/net_core/)。</span><span class="sxs-lookup"><span data-stu-id="64740-109">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="64740-110">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="64740-110">Install the .NET Core SDK</span></span>

<span data-ttu-id="64740-111">向訂閱管理員註冊之後，您就可以開始安裝和啟用 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="64740-111">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="64740-112">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="64740-112">In your terminal, run the following commands.</span></span>

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="64740-113">安裝 ASP.NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="64740-113">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="64740-114">向訂閱管理員註冊之後，您就可以開始安裝和啟用 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="64740-114">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="64740-115">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="64740-115">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="64740-116">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="64740-116">Install the .NET Core Runtime</span></span>

<span data-ttu-id="64740-117">向訂用帳戶管理員註冊之後，您就可以開始安裝和啟用 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="64740-117">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="64740-118">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="64740-118">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```

## <a name="see-also"></a><span data-ttu-id="64740-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="64740-119">See also</span></span>

- [<span data-ttu-id="64740-120">在 Red Hat Enterprise Linux 8 上使用 .NET Core 3。0</span><span class="sxs-lookup"><span data-stu-id="64740-120">Using .NET Core 3.0 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide_for_rhel_8/gs_install_dotnet)

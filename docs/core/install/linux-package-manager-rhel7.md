---
title: 在 Linux RHEL 7 套件管理員上安裝 .NET Core-.NET Core
description: 使用套件管理員，在 RHEL 7 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: cc7865727927eda1406da26e64b89325fd5665a4
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801965"
---
# <a name="rhel-7-package-manager---install-net-core"></a><span data-ttu-id="c0eca-103">RHEL 7 套件管理員-安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="c0eca-103">RHEL 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="c0eca-104">本文說明如何使用套件管理員，在 RHEL 7 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="c0eca-104">This article describes how to use a package manager to install .NET Core on RHEL 7.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="c0eca-105">註冊您的 Red Hat 訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="c0eca-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="c0eca-106">若要從 RHEL 上的 Red Hat 安裝 .NET Core，您必須先使用 Red Hat 訂用帳戶管理員進行註冊。</span><span class="sxs-lookup"><span data-stu-id="c0eca-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="c0eca-107">如果未在您的系統上完成此動作，或您不確定，請參閱[.Net Core 的 Red Hat 產品檔](https://access.redhat.com/documentation/net_core/)。</span><span class="sxs-lookup"><span data-stu-id="c0eca-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="c0eca-108">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c0eca-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="c0eca-109">向訂閱管理員註冊之後，您就可以開始安裝和啟用 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="c0eca-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="c0eca-110">在您的終端機中，執行下列命令以啟用 RHEL 7 dotnet 通道並安裝。</span><span class="sxs-lookup"><span data-stu-id="c0eca-110">In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install .</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="c0eca-111">安裝 ASP.NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="c0eca-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="c0eca-112">向訂閱管理員註冊之後，您就可以開始安裝和啟用 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="c0eca-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="c0eca-113">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c0eca-113">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-aspnetcore-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="c0eca-114">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="c0eca-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="c0eca-115">向訂用帳戶管理員註冊之後，您就可以開始安裝和啟用 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="c0eca-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="c0eca-116">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c0eca-116">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-dotnet-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="see-also"></a><span data-ttu-id="c0eca-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="c0eca-117">See also</span></span>

- [<span data-ttu-id="c0eca-118">在 Red Hat Enterprise Linux 7 上使用 .NET Core 3。0</span><span class="sxs-lookup"><span data-stu-id="c0eca-118">Using .NET Core 3.0 on Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide/gs_install_dotnet)

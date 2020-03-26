---
title: 在 Linux RHEL 7 套裝軟體管理器上安裝 .NET 核心 - .NET 核心
description: 使用包管理器在 RHEL 7 上安裝 .NET 核心 SDK 和運行時。
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: d1f1372b32c7b2471a96492d48aab5533dadb64a
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134207"
---
# <a name="rhel-7-package-manager---install-net-core"></a><span data-ttu-id="c0537-103">RHEL 7 套裝軟體管理器 - 安裝 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="c0537-103">RHEL 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="c0537-104">本文介紹如何使用包管理器在 RHEL 7 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="c0537-104">This article describes how to use a package manager to install .NET Core on RHEL 7.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="c0537-105">註冊您的紅帽訂閱</span><span class="sxs-lookup"><span data-stu-id="c0537-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="c0537-106">要在 RHEL 上安裝來自紅帽的 .NET 核心，首先需要使用紅帽訂閱管理器進行註冊。</span><span class="sxs-lookup"><span data-stu-id="c0537-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="c0537-107">如果系統上尚未完成此操作，或者不確定，請參閱[.NET Core 的紅帽產品文檔](https://access.redhat.com/documentation/net_core/)。</span><span class="sxs-lookup"><span data-stu-id="c0537-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="c0537-108">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c0537-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="c0537-109">向訂閱管理器註冊後，即可安裝並啟用 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="c0537-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="c0537-110">在終端中，運行以下命令以啟用 RHEL 7 點網通道並安裝。</span><span class="sxs-lookup"><span data-stu-id="c0537-110">In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="c0537-111">安裝ASP.NET核心運行時</span><span class="sxs-lookup"><span data-stu-id="c0537-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="c0537-112">向訂閱管理器註冊後，即可安裝並啟用ASP.NET核心運行時。</span><span class="sxs-lookup"><span data-stu-id="c0537-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="c0537-113">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="c0537-113">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="c0537-114">安裝 .NET 核心運行時</span><span class="sxs-lookup"><span data-stu-id="c0537-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="c0537-115">註冊訂閱管理器後，即可安裝並啟用 .NET 核心運行時。</span><span class="sxs-lookup"><span data-stu-id="c0537-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="c0537-116">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="c0537-116">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-dotnet-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="see-also"></a><span data-ttu-id="c0537-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0537-117">See also</span></span>

- [<span data-ttu-id="c0537-118">在紅帽企業 Linux 7 上使用 .NET 核心 3.1</span><span class="sxs-lookup"><span data-stu-id="c0537-118">Using .NET Core 3.1 on Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.1/html/getting_started_guide/gs_install_dotnet)

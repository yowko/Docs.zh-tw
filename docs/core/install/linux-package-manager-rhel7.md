---
title: 在 Linux RHEL 7 套裝軟體管理器上安裝 .NET 核心 - .NET 核心
description: 使用包管理器在 RHEL 7 上安裝 .NET 核心 SDK 和運行時。
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 4f85ed3da8a434fcd5b6ee88491daf623c3c8b31
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76980180"
---
# <a name="rhel-7-package-manager---install-net-core"></a><span data-ttu-id="7d093-103">RHEL 7 套裝軟體管理器 - 安裝 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="7d093-103">RHEL 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="7d093-104">本文介紹如何使用包管理器在 RHEL 7 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="7d093-104">This article describes how to use a package manager to install .NET Core on RHEL 7.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="7d093-105">註冊您的紅帽訂閱</span><span class="sxs-lookup"><span data-stu-id="7d093-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="7d093-106">要在 RHEL 上安裝來自紅帽的 .NET 核心，首先需要使用紅帽訂閱管理器進行註冊。</span><span class="sxs-lookup"><span data-stu-id="7d093-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="7d093-107">如果系統上尚未完成此操作，或者不確定，請參閱[.NET Core 的紅帽產品文檔](https://access.redhat.com/documentation/net_core/)。</span><span class="sxs-lookup"><span data-stu-id="7d093-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="7d093-108">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="7d093-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="7d093-109">向訂閱管理器註冊後，即可安裝並啟用 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="7d093-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="7d093-110">在終端中，運行以下命令以啟用 RHEL 7 點網通道並安裝。</span><span class="sxs-lookup"><span data-stu-id="7d093-110">In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="7d093-111">安裝ASP.NET核心運行時</span><span class="sxs-lookup"><span data-stu-id="7d093-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="7d093-112">向訂閱管理器註冊後，即可安裝並啟用ASP.NET核心運行時。</span><span class="sxs-lookup"><span data-stu-id="7d093-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="7d093-113">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="7d093-113">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="7d093-114">安裝 .NET 核心運行時</span><span class="sxs-lookup"><span data-stu-id="7d093-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="7d093-115">註冊訂閱管理器後，即可安裝並啟用 .NET 核心運行時。</span><span class="sxs-lookup"><span data-stu-id="7d093-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="7d093-116">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="7d093-116">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-dotnet-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="see-also"></a><span data-ttu-id="7d093-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d093-117">See also</span></span>

- [<span data-ttu-id="7d093-118">在紅帽企業 Linux 7 上使用 .NET 核心 3.1</span><span class="sxs-lookup"><span data-stu-id="7d093-118">Using .NET Core 3.1 on Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.1/html/getting_started_guide/gs_install_dotnet)

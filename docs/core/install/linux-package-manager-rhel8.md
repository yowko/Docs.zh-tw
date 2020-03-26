---
title: 在 Linux RHEL 8 套裝軟體管理器上安裝 .NET 核心 - .NET 核心
description: 使用包管理器在 RHEL 8 上安裝 .NET 核心 SDK 和運行時。
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: b564a386eb67b6e414a832ad3bca10d3d09022bd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134198"
---
# <a name="rhel-8-package-manager---install-net-core"></a><span data-ttu-id="f1827-103">RHEL 8 套裝軟體管理器 - 安裝 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="f1827-103">RHEL 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="f1827-104">本文介紹如何使用包管理器在 RHEL 8 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="f1827-104">This article describes how to use a package manager to install .NET Core on RHEL 8.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="f1827-105">註冊您的紅帽訂閱</span><span class="sxs-lookup"><span data-stu-id="f1827-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="f1827-106">要在 RHEL 上安裝來自紅帽的 .NET 核心，首先需要使用紅帽訂閱管理器進行註冊。</span><span class="sxs-lookup"><span data-stu-id="f1827-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="f1827-107">如果系統上尚未完成此操作，或者不確定，請參閱[.NET Core 的紅帽產品文檔](https://access.redhat.com/documentation/net_core/)。</span><span class="sxs-lookup"><span data-stu-id="f1827-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="f1827-108">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="f1827-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="f1827-109">向訂閱管理器註冊後，即可安裝並啟用 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="f1827-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="f1827-110">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="f1827-110">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="f1827-111">安裝ASP.NET核心運行時</span><span class="sxs-lookup"><span data-stu-id="f1827-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="f1827-112">向訂閱管理器註冊後，即可安裝並啟用ASP.NET核心運行時。</span><span class="sxs-lookup"><span data-stu-id="f1827-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="f1827-113">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="f1827-113">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="f1827-114">安裝 .NET 核心運行時</span><span class="sxs-lookup"><span data-stu-id="f1827-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="f1827-115">註冊訂閱管理器後，即可安裝並啟用 .NET 核心運行時。</span><span class="sxs-lookup"><span data-stu-id="f1827-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="f1827-116">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="f1827-116">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install dotnet-runtime-3.1
```

## <a name="see-also"></a><span data-ttu-id="f1827-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1827-117">See also</span></span>

- [<span data-ttu-id="f1827-118">在紅帽企業 Linux 8 上使用 .NET 核心 3.1</span><span class="sxs-lookup"><span data-stu-id="f1827-118">Using .NET Core 3.1 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)

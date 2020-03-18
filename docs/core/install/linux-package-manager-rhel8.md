---
title: 在 Linux RHEL 8 套裝軟體管理器上安裝 .NET 核心 - .NET 核心
description: 使用包管理器在 RHEL 8 上安裝 .NET 核心 SDK 和運行時。
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 054494a9b77e1c7803e42c947e067d3eb290f73c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78849807"
---
# <a name="rhel-8-package-manager---install-net-core"></a><span data-ttu-id="c600b-103">RHEL 8 套裝軟體管理器 - 安裝 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="c600b-103">RHEL 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="c600b-104">本文介紹如何使用包管理器在 RHEL 8 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="c600b-104">This article describes how to use a package manager to install .NET Core on RHEL 8.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="c600b-105">註冊您的紅帽訂閱</span><span class="sxs-lookup"><span data-stu-id="c600b-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="c600b-106">要在 RHEL 上安裝來自紅帽的 .NET 核心，首先需要使用紅帽訂閱管理器進行註冊。</span><span class="sxs-lookup"><span data-stu-id="c600b-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="c600b-107">如果系統上尚未完成此操作，或者不確定，請參閱[.NET Core 的紅帽產品文檔](https://access.redhat.com/documentation/net_core/)。</span><span class="sxs-lookup"><span data-stu-id="c600b-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="c600b-108">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c600b-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="c600b-109">向訂閱管理器註冊後，即可安裝並啟用 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="c600b-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="c600b-110">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="c600b-110">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="c600b-111">安裝ASP.NET核心運行時</span><span class="sxs-lookup"><span data-stu-id="c600b-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="c600b-112">向訂閱管理器註冊後，即可安裝並啟用ASP.NET核心運行時。</span><span class="sxs-lookup"><span data-stu-id="c600b-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="c600b-113">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="c600b-113">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="c600b-114">安裝 .NET 核心運行時</span><span class="sxs-lookup"><span data-stu-id="c600b-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="c600b-115">註冊訂閱管理器後，即可安裝並啟用 .NET 核心運行時。</span><span class="sxs-lookup"><span data-stu-id="c600b-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="c600b-116">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="c600b-116">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install dotnet-runtime-3.1
```

## <a name="see-also"></a><span data-ttu-id="c600b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c600b-117">See also</span></span>

- [<span data-ttu-id="c600b-118">在紅帽企業 Linux 8 上使用 .NET 核心 3.1</span><span class="sxs-lookup"><span data-stu-id="c600b-118">Using .NET Core 3.1 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)

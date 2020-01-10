---
title: 在 openSUSE 15 上安裝 .NET Core-套件管理員-.NET Core
description: 使用套件管理員在 openSUSE 15 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 12/26/2019
ms.openlocfilehash: cba07bafc32cc71a1cdaec08902284e105af4776
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740665"
---
# <a name="opensuse-15-package-manager---install-net-core"></a><span data-ttu-id="74502-103">openSUSE 15 套件管理員-安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="74502-103">openSUSE 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="74502-104">本文說明如何使用套件管理員，在 openSUSE 15 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="74502-104">This article describes how to use a package manager to install .NET Core on openSUSE 15.</span></span> <span data-ttu-id="74502-105">如果您要安裝執行時間，我們建議您安裝[ASP.NET Core 運行](#install-the-aspnet-core-runtime)時間，因為它同時包含 .net Core 和 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="74502-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="74502-106">註冊 Microsoft 金鑰和總結</span><span class="sxs-lookup"><span data-stu-id="74502-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="74502-107">安裝 .NET 之前，您必須：</span><span class="sxs-lookup"><span data-stu-id="74502-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="74502-108">註冊 Microsoft 金鑰。</span><span class="sxs-lookup"><span data-stu-id="74502-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="74502-109">註冊產品存放庫。</span><span class="sxs-lookup"><span data-stu-id="74502-109">Register the product repository.</span></span>
- <span data-ttu-id="74502-110">安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="74502-110">Install required dependencies.</span></span>

<span data-ttu-id="74502-111">每部電腦只需要執行這項作業一次。</span><span class="sxs-lookup"><span data-stu-id="74502-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="74502-112">開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="74502-112">Open a terminal and run the following commands.</span></span>

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget -q https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="dependency-error-with-net-core-31"></a><span data-ttu-id="74502-113">.NET Core 3.1 的相依性錯誤</span><span class="sxs-lookup"><span data-stu-id="74502-113">Dependency error with .NET Core 3.1</span></span>

<span data-ttu-id="74502-114">適用于 openSUSE 的 .NET Core 3.1 套件摘要發生**krb5**相依性問題。</span><span class="sxs-lookup"><span data-stu-id="74502-114">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="74502-115">在安裝 .NET Core 3.1 或 ASP.NET Core 3.1 之前，請使用下列命令來安裝正確的相依性。</span><span class="sxs-lookup"><span data-stu-id="74502-115">Use the following command to install the correct dependencies prior to installing .NET Core 3.1 or ASP.NET Core 3.1.</span></span>

```bash
sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="74502-116">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="74502-116">Install the .NET Core SDK</span></span>

<span data-ttu-id="74502-117">更新可供安裝的產品，然後安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="74502-117">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="74502-118">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="74502-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="74502-119">適用于 openSUSE 的 .NET Core 3.1 套件摘要發生**krb5**相依性問題。</span><span class="sxs-lookup"><span data-stu-id="74502-119">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="74502-120">使用下列命令來安裝正確的相依性，然後安裝 .NET Core 3.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="74502-120">Use the following command to install the correct dependencies, then install the .NET Core 3.1 SDK.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="74502-121">安裝 ASP.NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="74502-121">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="74502-122">更新可供安裝的產品，然後安裝 ASP.NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="74502-122">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="74502-123">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="74502-123">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="74502-124">適用于 openSUSE 的 .NET Core 3.1 套件摘要發生**krb5**相依性問題。</span><span class="sxs-lookup"><span data-stu-id="74502-124">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="74502-125">使用下列命令來安裝正確的相依性，然後安裝 ASP.NET Core 3.1 執行時間。</span><span class="sxs-lookup"><span data-stu-id="74502-125">Use the following command to install the correct dependencies, then install the ASP.NET Core 3.1 runtime.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="74502-126">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="74502-126">Install the .NET Core runtime</span></span>

<span data-ttu-id="74502-127">更新可供安裝的產品，然後安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="74502-127">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="74502-128">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="74502-128">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="74502-129">適用于 openSUSE 的 .NET Core 3.1 套件摘要發生**krb5**相依性問題。</span><span class="sxs-lookup"><span data-stu-id="74502-129">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="74502-130">使用下列命令來安裝正確的相依性，然後安裝 .NET Core 3.1 執行時間。</span><span class="sxs-lookup"><span data-stu-id="74502-130">Use the following command to install the correct dependencies, then install the .NET Core 3.1 runtime.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="74502-131">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="74502-131">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

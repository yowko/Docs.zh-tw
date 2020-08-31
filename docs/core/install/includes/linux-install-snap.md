---
ms.openlocfilehash: 5e77b7bd73c09e061a94a29703cf5286814d1ebb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602912"
---

[<span data-ttu-id="c9b5b-101">您可以從「貼齊」存放區使用 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-101">.NET Core is available from the Snap Store.</span></span>](https://snapcraft.io/dotnet-sdk)

<span data-ttu-id="c9b5b-102">「貼齊」是應用程式及其相依性的組合，可在不需要跨多個不同 Linux 發行版本進行修改的情況下運作。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-102">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="c9b5b-103">快照可從貼齊存放區中探索並安裝。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-103">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="c9b5b-104">如需貼齊的詳細資訊，請參閱 [開始使用嵌入式管理單元](https://snapcraft.io/docs/getting-started)。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-104">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

<span data-ttu-id="c9b5b-105">只有支援的 .NET Core 版本可透過 [貼齊] 使用。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-105">Only supported versions of .NET Core are available through Snap.</span></span>

### <a name="install-the-sdk"></a><span data-ttu-id="c9b5b-106">安裝 SDK</span><span class="sxs-lookup"><span data-stu-id="c9b5b-106">Install the SDK</span></span>

<span data-ttu-id="c9b5b-107">.NET Core SDK 的貼齊套件都會在相同的識別碼下發布： `dotnet-sdk` 。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-107">Snap packages for .NET Core SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="c9b5b-108">您可以藉由指定通道來安裝特定版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-108">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="c9b5b-109">SDK 包含 coresponding 執行時間。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-109">The SDK includes the coresponding runtime.</span></span> <span data-ttu-id="c9b5b-110">下表列出通道：</span><span class="sxs-lookup"><span data-stu-id="c9b5b-110">The following table list the channels:</span></span>

| <span data-ttu-id="c9b5b-111">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="c9b5b-111">.NET Core version</span></span> | <span data-ttu-id="c9b5b-112">貼齊套件</span><span class="sxs-lookup"><span data-stu-id="c9b5b-112">Snap package</span></span>             |
|-------------------|--------------------------|
| <span data-ttu-id="c9b5b-113">3.1 (LTS) </span><span class="sxs-lookup"><span data-stu-id="c9b5b-113">3.1 (LTS)</span></span>         | <span data-ttu-id="c9b5b-114">`3.1` 或 `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="c9b5b-114">`3.1` or `latest/stable`</span></span> |
| <span data-ttu-id="c9b5b-115">2.1 (LTS) </span><span class="sxs-lookup"><span data-stu-id="c9b5b-115">2.1 (LTS)</span></span>         | `2.1`                    |
| <span data-ttu-id="c9b5b-116">.NET 5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="c9b5b-116">.NET 5.0 preview</span></span>  | `5.0/beta`               |

<span data-ttu-id="c9b5b-117">使用 `snap install` 命令安裝 .NET Core SDK 的嵌入式管理套件。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-117">Use the `snap install` command to install a .NET Core SDK snap package.</span></span> <span data-ttu-id="c9b5b-118">使用 `--channel` 參數來指出要安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-118">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="c9b5b-119">如果省略此參數， `latest/stable` 則會使用。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-119">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="c9b5b-120">在此範例中， `3.1` 指定了：</span><span class="sxs-lookup"><span data-stu-id="c9b5b-120">In this example, `3.1` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=3.1
```

<span data-ttu-id="c9b5b-121">接下來， `dotnet` 使用下列命令註冊系統的命令 `snap alias` ：</span><span class="sxs-lookup"><span data-stu-id="c9b5b-121">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="c9b5b-122">此命令的格式為： `sudo snap alias {package}.{command} {alias}` 。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-122">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="c9b5b-123">您可以選擇任何想要 `{alias}` 的名稱。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-123">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="c9b5b-124">例如，您可以在由 snap：進行安裝的特定版本之後，將命令命名為 `sudo snap alias dotnet-sdk.dotnet dotnet31` 。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-124">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet31`.</span></span> <span data-ttu-id="c9b5b-125">當您使用命令時 `dotnet31` ，將會叫用這個特定的 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-125">When you use the command `dotnet31`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="c9b5b-126">但是，這與大部分的教學課程和範例都不相容，因為它們預期 `dotnet` 會有命令可供使用。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-126">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="c9b5b-127">安裝執行階段</span><span class="sxs-lookup"><span data-stu-id="c9b5b-127">Install the runtime</span></span>

<span data-ttu-id="c9b5b-128">適用于 .NET Core 執行時間的貼齊套件會在其專屬套件識別碼下發布。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-128">Snap packages for .NET Core Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="c9b5b-129">下表列出封裝識別碼：</span><span class="sxs-lookup"><span data-stu-id="c9b5b-129">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="c9b5b-130">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="c9b5b-130">.NET Core version</span></span> | <span data-ttu-id="c9b5b-131">貼齊套件</span><span class="sxs-lookup"><span data-stu-id="c9b5b-131">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="c9b5b-132">3.1 (LTS) </span><span class="sxs-lookup"><span data-stu-id="c9b5b-132">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="c9b5b-133">3.0</span><span class="sxs-lookup"><span data-stu-id="c9b5b-133">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="c9b5b-134">2.2</span><span class="sxs-lookup"><span data-stu-id="c9b5b-134">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="c9b5b-135">2.1 (LTS) </span><span class="sxs-lookup"><span data-stu-id="c9b5b-135">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="c9b5b-136">使用 `snap install` 命令來安裝 .Net Core 執行時間嵌入式管理套件。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-136">Use the `snap install` command to install a .NET Core Runtime snap package.</span></span> <span data-ttu-id="c9b5b-137">在此範例中，已安裝 .NET Core 3.1：</span><span class="sxs-lookup"><span data-stu-id="c9b5b-137">In this example, .NET Core 3.1 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-31 --classic
```

<span data-ttu-id="c9b5b-138">接下來， `dotnet` 使用下列命令註冊系統的命令 `snap alias` ：</span><span class="sxs-lookup"><span data-stu-id="c9b5b-138">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-31.dotnet dotnet
```

<span data-ttu-id="c9b5b-139">此命令的格式為： `sudo snap alias {package}.{command} {alias}` 。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-139">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="c9b5b-140">您可以選擇任何想要 `{alias}` 的名稱。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-140">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="c9b5b-141">例如，您可以在由 snap：進行安裝的特定版本之後，將命令命名為 `sudo snap alias dotnet-runtime-31.dotnet dotnet31` 。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-141">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-31.dotnet dotnet31`.</span></span> <span data-ttu-id="c9b5b-142">當您使用命令時 `dotnet31` ，將會叫用這個特定的 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-142">When you use the command `dotnet31`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="c9b5b-143">但是，這與大部分的教學課程和範例都不相容，因為它們預期 `dotnet` 會有命令可供使用。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-143">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="ssl-certificate-errors"></a><span data-ttu-id="c9b5b-144">SSL 憑證錯誤</span><span class="sxs-lookup"><span data-stu-id="c9b5b-144">SSL Certificate errors</span></span>

<span data-ttu-id="c9b5b-145">透過 [貼齊] 安裝 .NET 時，可能會在某些散發版本上找不到 .NET SSL 憑證，而且您可能會在下列情況收到類似下面的錯誤 `restore` ：</span><span class="sxs-lookup"><span data-stu-id="c9b5b-145">When .NET is installed through Snap, it's possible that on some distros the .NET SSL certificates may not be found and you may receive an error similar to the following during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="c9b5b-146">若要解決此問題，請設定一些環境變數：</span><span class="sxs-lookup"><span data-stu-id="c9b5b-146">To resolve this issue, set a few enviornment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="c9b5b-147">憑證位置會因發行版本而異。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-147">The certificate location will vary by distro.</span></span> <span data-ttu-id="c9b5b-148">以下是我們遇到問題的散發版本位置。</span><span class="sxs-lookup"><span data-stu-id="c9b5b-148">Here are the locations for the distros where we have experienced the issue.</span></span>

* <span data-ttu-id="c9b5b-149">Fedora `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="c9b5b-149">Fedora - `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span></span>
* <span data-ttu-id="c9b5b-150">OpenSUSE `/etc/ssl/ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="c9b5b-150">OpenSUSE - `/etc/ssl/ca-bundle.pem`</span></span>
* <span data-ttu-id="c9b5b-151">Solus - `/etc/ssl/certs/ca-certificates.crt`</span><span class="sxs-lookup"><span data-stu-id="c9b5b-151">Solus - `/etc/ssl/certs/ca-certificates.crt`</span></span>

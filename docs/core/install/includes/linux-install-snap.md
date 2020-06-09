---
ms.openlocfilehash: 5e77b7bd73c09e061a94a29703cf5286814d1ebb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602912"
---

<span data-ttu-id="24f44-101">[您可以從 [貼齊存放區] 取得 .NET Core。](https://snapcraft.io/dotnet-sdk)</span><span class="sxs-lookup"><span data-stu-id="24f44-101">[.NET Core is available from the Snap Store.](https://snapcraft.io/dotnet-sdk)</span></span>

<span data-ttu-id="24f44-102">「貼齊」是應用程式及其相依性的組合，不需要在許多不同的 Linux 散發套件上進行修改即可運作。</span><span class="sxs-lookup"><span data-stu-id="24f44-102">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="24f44-103">您可以從 [貼齊存放區] 探索和安裝快照。</span><span class="sxs-lookup"><span data-stu-id="24f44-103">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="24f44-104">如需有關貼齊的詳細資訊，請參閱[開始使用貼齊](https://snapcraft.io/docs/getting-started)。</span><span class="sxs-lookup"><span data-stu-id="24f44-104">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

<span data-ttu-id="24f44-105">只有支援的 .NET Core 版本可透過 [貼齊] 取得。</span><span class="sxs-lookup"><span data-stu-id="24f44-105">Only supported versions of .NET Core are available through Snap.</span></span>

### <a name="install-the-sdk"></a><span data-ttu-id="24f44-106">安裝 SDK</span><span class="sxs-lookup"><span data-stu-id="24f44-106">Install the SDK</span></span>

<span data-ttu-id="24f44-107">.NET Core SDK 的貼齊封裝都是以相同的識別碼發佈： `dotnet-sdk` 。</span><span class="sxs-lookup"><span data-stu-id="24f44-107">Snap packages for .NET Core SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="24f44-108">您可以藉由指定通道來安裝特定版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="24f44-108">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="24f44-109">SDK 包含 coresponding 執行時間。</span><span class="sxs-lookup"><span data-stu-id="24f44-109">The SDK includes the coresponding runtime.</span></span> <span data-ttu-id="24f44-110">下表列出通道：</span><span class="sxs-lookup"><span data-stu-id="24f44-110">The following table list the channels:</span></span>

| <span data-ttu-id="24f44-111">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="24f44-111">.NET Core version</span></span> | <span data-ttu-id="24f44-112">貼齊套件</span><span class="sxs-lookup"><span data-stu-id="24f44-112">Snap package</span></span>             |
|-------------------|--------------------------|
| <span data-ttu-id="24f44-113">3.1 （LTS）</span><span class="sxs-lookup"><span data-stu-id="24f44-113">3.1 (LTS)</span></span>         | <span data-ttu-id="24f44-114">`3.1` 或 `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="24f44-114">`3.1` or `latest/stable`</span></span> |
| <span data-ttu-id="24f44-115">2.1 （LTS）</span><span class="sxs-lookup"><span data-stu-id="24f44-115">2.1 (LTS)</span></span>         | `2.1`                    |
| <span data-ttu-id="24f44-116">.NET 5.0 preview</span><span class="sxs-lookup"><span data-stu-id="24f44-116">.NET 5.0 preview</span></span>  | `5.0/beta`               |

<span data-ttu-id="24f44-117">使用 `snap install` 命令來安裝 .NET Core SDK 的貼齊套件。</span><span class="sxs-lookup"><span data-stu-id="24f44-117">Use the `snap install` command to install a .NET Core SDK snap package.</span></span> <span data-ttu-id="24f44-118">使用 `--channel` 參數來指出要安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="24f44-118">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="24f44-119">如果省略此參數， `latest/stable` 則會使用。</span><span class="sxs-lookup"><span data-stu-id="24f44-119">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="24f44-120">在此範例中， `3.1` 會指定：</span><span class="sxs-lookup"><span data-stu-id="24f44-120">In this example, `3.1` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=3.1
```

<span data-ttu-id="24f44-121">接下來， `dotnet` 使用命令來註冊系統的命令 `snap alias` ：</span><span class="sxs-lookup"><span data-stu-id="24f44-121">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="24f44-122">此命令的格式為： `sudo snap alias {package}.{command} {alias}` 。</span><span class="sxs-lookup"><span data-stu-id="24f44-122">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="24f44-123">您可以選擇您想要 `{alias}` 的任何名稱。</span><span class="sxs-lookup"><span data-stu-id="24f44-123">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="24f44-124">例如，您可以在 [貼齊：] 安裝的特定版本之後，將命令命名為 `sudo snap alias dotnet-sdk.dotnet dotnet31` 。</span><span class="sxs-lookup"><span data-stu-id="24f44-124">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet31`.</span></span> <span data-ttu-id="24f44-125">當您使用命令時 `dotnet31` ，您將會叫用此特定版本的 .net。</span><span class="sxs-lookup"><span data-stu-id="24f44-125">When you use the command `dotnet31`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="24f44-126">但這與大部分的教學課程和範例不相容，因為它們預期 `dotnet` 會有命令可供使用。</span><span class="sxs-lookup"><span data-stu-id="24f44-126">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="24f44-127">安裝執行階段</span><span class="sxs-lookup"><span data-stu-id="24f44-127">Install the runtime</span></span>

<span data-ttu-id="24f44-128">.NET Core 執行時間的貼齊套件會分別以自己的套件識別碼發行。</span><span class="sxs-lookup"><span data-stu-id="24f44-128">Snap packages for .NET Core Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="24f44-129">下表列出套件識別碼：</span><span class="sxs-lookup"><span data-stu-id="24f44-129">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="24f44-130">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="24f44-130">.NET Core version</span></span> | <span data-ttu-id="24f44-131">貼齊套件</span><span class="sxs-lookup"><span data-stu-id="24f44-131">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="24f44-132">3.1 （LTS）</span><span class="sxs-lookup"><span data-stu-id="24f44-132">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="24f44-133">3.0</span><span class="sxs-lookup"><span data-stu-id="24f44-133">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="24f44-134">2.2</span><span class="sxs-lookup"><span data-stu-id="24f44-134">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="24f44-135">2.1 （LTS）</span><span class="sxs-lookup"><span data-stu-id="24f44-135">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="24f44-136">使用 `snap install` 命令來安裝 .Net Core 執行時間嵌入式管理套件。</span><span class="sxs-lookup"><span data-stu-id="24f44-136">Use the `snap install` command to install a .NET Core Runtime snap package.</span></span> <span data-ttu-id="24f44-137">在此範例中，會安裝 .NET Core 3.1：</span><span class="sxs-lookup"><span data-stu-id="24f44-137">In this example, .NET Core 3.1 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-31 --classic
```

<span data-ttu-id="24f44-138">接下來， `dotnet` 使用命令來註冊系統的命令 `snap alias` ：</span><span class="sxs-lookup"><span data-stu-id="24f44-138">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-31.dotnet dotnet
```

<span data-ttu-id="24f44-139">此命令的格式為： `sudo snap alias {package}.{command} {alias}` 。</span><span class="sxs-lookup"><span data-stu-id="24f44-139">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="24f44-140">您可以選擇您想要 `{alias}` 的任何名稱。</span><span class="sxs-lookup"><span data-stu-id="24f44-140">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="24f44-141">例如，您可以在 [貼齊：] 安裝的特定版本之後，將命令命名為 `sudo snap alias dotnet-runtime-31.dotnet dotnet31` 。</span><span class="sxs-lookup"><span data-stu-id="24f44-141">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-31.dotnet dotnet31`.</span></span> <span data-ttu-id="24f44-142">當您使用命令時 `dotnet31` ，您將會叫用此特定版本的 .net。</span><span class="sxs-lookup"><span data-stu-id="24f44-142">When you use the command `dotnet31`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="24f44-143">但這與大部分的教學課程和範例不相容，因為它們預期 `dotnet` 會有命令可供使用。</span><span class="sxs-lookup"><span data-stu-id="24f44-143">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="ssl-certificate-errors"></a><span data-ttu-id="24f44-144">SSL 憑證錯誤</span><span class="sxs-lookup"><span data-stu-id="24f44-144">SSL Certificate errors</span></span>

<span data-ttu-id="24f44-145">透過貼齊安裝 .NET 時，可能會在某些散發版本上找不到 .NET SSL 憑證，而且您可能會在下列情況收到類似以下的錯誤 `restore` ：</span><span class="sxs-lookup"><span data-stu-id="24f44-145">When .NET is installed through Snap, it's possible that on some distros the .NET SSL certificates may not be found and you may receive an error similar to the following during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="24f44-146">若要解決此問題，請設定幾個環境變數：</span><span class="sxs-lookup"><span data-stu-id="24f44-146">To resolve this issue, set a few enviornment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="24f44-147">憑證位置會因散發版本而異。</span><span class="sxs-lookup"><span data-stu-id="24f44-147">The certificate location will vary by distro.</span></span> <span data-ttu-id="24f44-148">以下是我們遇到此問題的散發版本位置。</span><span class="sxs-lookup"><span data-stu-id="24f44-148">Here are the locations for the distros where we have experienced the issue.</span></span>

* <span data-ttu-id="24f44-149">Fedora`/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="24f44-149">Fedora - `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span></span>
* <span data-ttu-id="24f44-150">OpenSUSE`/etc/ssl/ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="24f44-150">OpenSUSE - `/etc/ssl/ca-bundle.pem`</span></span>
* <span data-ttu-id="24f44-151">Solus -`/etc/ssl/certs/ca-certificates.crt`</span><span class="sxs-lookup"><span data-stu-id="24f44-151">Solus - `/etc/ssl/certs/ca-certificates.crt`</span></span>

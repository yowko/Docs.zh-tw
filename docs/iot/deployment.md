---
title: 將 .NET 應用程式部署至 Raspberry Pi
description: 瞭解如何將 .NET 應用程式部署至 Raspberry Pi。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
ms.openlocfilehash: 4da558e2cdfc283d21f2a5497cb71dc746109614
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96586663"
---
# <a name="deploy-net-apps-to-raspberry-pi"></a><span data-ttu-id="ad918-103">將 .NET 應用程式部署至 Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="ad918-103">Deploy .NET apps to Raspberry Pi</span></span>

<span data-ttu-id="ad918-104">將 .NET 應用程式部署到 Raspberry Pi 與任何其他平臺的部署完全相同。</span><span class="sxs-lookup"><span data-stu-id="ad918-104">Deployment of .NET apps to Raspberry Pi is identical to that of any other platform.</span></span> <span data-ttu-id="ad918-105">您的應用程式可以執行為 *獨立* 或 *架構相依的* 部署模式。</span><span class="sxs-lookup"><span data-stu-id="ad918-105">Your app can run as *self-contained* or *framework-dependent* deployment modes.</span></span> <span data-ttu-id="ad918-106">每個策略都有其優點。</span><span class="sxs-lookup"><span data-stu-id="ad918-106">There are advantages to each strategy.</span></span> <span data-ttu-id="ad918-107">如需詳細資訊，請參閱 [.net 應用程式發行總覽](../core/deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ad918-107">For more information, see [.NET application publishing overview](../core/deploying/index.md).</span></span>

## <a name="deploying-a-framework-dependent-app"></a><span data-ttu-id="ad918-108">部署與 framework 相依的應用程式</span><span class="sxs-lookup"><span data-stu-id="ad918-108">Deploying a framework-dependent app</span></span>

<span data-ttu-id="ad918-109">若要將您的應用程式部署為與 framework 相依的應用程式，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="ad918-109">To deploy your app as a framework-dependent app, complete the following steps:</span></span>

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. <span data-ttu-id="ad918-110">使用 [dotnet 安裝腳本](../core/tools/dotnet-install-script.md)，在 Raspberry Pi 上安裝 .net。</span><span class="sxs-lookup"><span data-stu-id="ad918-110">Install .NET on the Raspberry Pi using the [dotnet-install scripts](../core/tools/dotnet-install-script.md).</span></span> <span data-ttu-id="ad918-111">從 Raspberry Pi (本機或 SSH) 上的 Bash 提示字元完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="ad918-111">Complete the following steps from a Bash prompt on the Raspberry Pi (local or SSH):</span></span>
    1. <span data-ttu-id="ad918-112">執行下列命令以安裝 .NET：</span><span class="sxs-lookup"><span data-stu-id="ad918-112">Run the following command to install .NET:</span></span>

        ```bash
        curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin
        ```

        > [!NOTE]
        > <span data-ttu-id="ad918-113">這會安裝最新版本。</span><span class="sxs-lookup"><span data-stu-id="ad918-113">This installs the latest version.</span></span> <span data-ttu-id="ad918-114">如果您需要特定版本，請新增 `--version <VERSION>` 至結尾，其中 `<VERSION>` 是特定的組建版本。</span><span class="sxs-lookup"><span data-stu-id="ad918-114">If you need a specific version, add `--version <VERSION>` to the end, where `<VERSION>` is the specific build version.</span></span>

    1. <span data-ttu-id="ad918-115">若要簡化路徑解析，請新增 `DOTNET_ROOT` 環境變數，並使用下列命令將 *dotnet* 目錄新增至 `$PATH` ：</span><span class="sxs-lookup"><span data-stu-id="ad918-115">To simplify path resolution, add a `DOTNET_ROOT` environment variable and add the *.dotnet* directory to `$PATH` with the following commands:</span></span>

        ```bash
        echo 'export DOTNET_ROOT=$HOME/.dotnet' >> ~/.bashrc
        echo 'export PATH=$PATH:$HOME/.dotnet' >> ~/.bashrc
        source ~/.bashrc
        ```

    1. <span data-ttu-id="ad918-116">使用下列命令確認 .NET 安裝：</span><span class="sxs-lookup"><span data-stu-id="ad918-116">Verify the .NET installation with the following command:</span></span>

        ```dotnetcli
        dotnet --version
        ```

        <span data-ttu-id="ad918-117">確認顯示的版本符合您安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="ad918-117">Verify the displayed version matches the version you installed.</span></span>

1. <span data-ttu-id="ad918-118">根據開發環境，在開發電腦上發佈應用程式，如下所示。</span><span class="sxs-lookup"><span data-stu-id="ad918-118">Publish the app on the development computer as follows, depending on development environment.</span></span>
    - <span data-ttu-id="ad918-119">如果使用 **Visual Studio**，請將 [應用程式部署至本機資料夾](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019)。</span><span class="sxs-lookup"><span data-stu-id="ad918-119">If using **Visual Studio**, [deploy the app to a local folder](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span></span> <span data-ttu-id="ad918-120">在發佈之前，請在發行設定檔摘要中選取 [ **編輯** ]，然後選取 [ **設定** ] 索引標籤。確認 **部署模式** 設定為 [ *Framework 相依* ]，並將 [ **目標運行** 時間] 設定為 [ *可移植*]。</span><span class="sxs-lookup"><span data-stu-id="ad918-120">Before publishing, select **Edit** in the publish profile summary and select the **Settings** tab. Ensure that **Deployment mode** is set to *Framework-dependent* and **Target runtime** is set to *Portable*.</span></span>
    - <span data-ttu-id="ad918-121">如果使用 **.NET CLI**，請使用 [dotnet publish](../core/tools/dotnet-publish.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="ad918-121">If using the **.NET CLI**, use the [dotnet publish](../core/tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="ad918-122">不需要額外的引數。</span><span class="sxs-lookup"><span data-stu-id="ad918-122">No additional arguments are required.</span></span>

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. <span data-ttu-id="ad918-123">從 Raspberry Pi (本機或 SSH) 的 Bash 提示字元中，執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad918-123">From a Bash prompt on the Raspberry Pi (local or SSH), run the app.</span></span> <span data-ttu-id="ad918-124">若要這樣做，請將部署資料夾設定為目前的目錄，然後執行下列命令 (其中 *HelloWorld.dll* 是應用程式) 的進入點：</span><span class="sxs-lookup"><span data-stu-id="ad918-124">To do this, set the deployment folder as the current directory and execute the following command (where *HelloWorld.dll* is the entry point of the app):</span></span>

    ```dotnetcli
    dotnet HelloWorld.dll
    ```

## <a name="deploying-a-self-contained-app"></a><span data-ttu-id="ad918-125">部署獨立式應用程式</span><span class="sxs-lookup"><span data-stu-id="ad918-125">Deploying a self-contained app</span></span>

<span data-ttu-id="ad918-126">若要將您的應用程式部署為獨立應用程式，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="ad918-126">To deploy your app as a self-contained app, complete the following steps:</span></span>

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. <span data-ttu-id="ad918-127">根據開發環境，在開發電腦上發佈應用程式，如下所示。</span><span class="sxs-lookup"><span data-stu-id="ad918-127">Publish the app on the development computer as follows, depending on development environment.</span></span>
    - <span data-ttu-id="ad918-128">如果使用 **Visual Studio**，請將 [應用程式部署至本機資料夾](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019)。</span><span class="sxs-lookup"><span data-stu-id="ad918-128">If using **Visual Studio**, [deploy the app to a local folder](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span></span> <span data-ttu-id="ad918-129">在發佈之前，請在發行設定檔摘要中選取 [ **編輯** ]，然後選取 [ **設定** ] 索引標籤。確認 **部署模式** 設定為 *獨立* ，而 **目標運行** 時間設定為 *linux-arm*。</span><span class="sxs-lookup"><span data-stu-id="ad918-129">Before publishing, select **Edit** in the publish profile summary and select the **Settings** tab. Ensure that **Deployment mode** is set to *Self-contained* and **Target runtime** is set to *linux-arm*.</span></span>
    - <span data-ttu-id="ad918-130">如果使用 **.NET CLI**，請使用 [dotnet publish](../core/tools/dotnet-publish.md) 命令搭配 `-r linux-arm` 引數：</span><span class="sxs-lookup"><span data-stu-id="ad918-130">If using the **.NET CLI**, use the [dotnet publish](../core/tools/dotnet-publish.md) command with the `-r linux-arm` argument:</span></span>

        ```dotnetcli
        dotnet publish -r linux-arm
        ```

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. <span data-ttu-id="ad918-131">從 Raspberry Pi (本機或 SSH) 的 Bash 提示字元中，執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad918-131">From a Bash prompt on the Raspberry Pi (local or SSH), run the app.</span></span> <span data-ttu-id="ad918-132">若要這樣做，請將目前目錄設定為部署位置，然後完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="ad918-132">To do this, set the current directory to the deployment location and complete the following steps:</span></span>
    1. <span data-ttu-id="ad918-133">提供可執行檔 *execute* 許可權 (其中 `HelloWorld` 是可執行檔的名稱) 。</span><span class="sxs-lookup"><span data-stu-id="ad918-133">Give the executable *execute* permission (where `HelloWorld` is the executable file name).</span></span>

        ```bash
        chmod +x HelloWorld
        ```

    1. <span data-ttu-id="ad918-134">執行可執行檔。</span><span class="sxs-lookup"><span data-stu-id="ad918-134">Run the executable.</span></span>

        ```bash
        ./HelloWorld
        ```

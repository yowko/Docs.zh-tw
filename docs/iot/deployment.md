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
# <a name="deploy-net-apps-to-raspberry-pi"></a>將 .NET 應用程式部署至 Raspberry Pi

將 .NET 應用程式部署到 Raspberry Pi 與任何其他平臺的部署完全相同。 您的應用程式可以執行為 *獨立* 或 *架構相依的* 部署模式。 每個策略都有其優點。 如需詳細資訊，請參閱 [.net 應用程式發行總覽](../core/deploying/index.md)。

## <a name="deploying-a-framework-dependent-app"></a>部署與 framework 相依的應用程式

若要將您的應用程式部署為與 framework 相依的應用程式，請完成下列步驟：

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. 使用 [dotnet 安裝腳本](../core/tools/dotnet-install-script.md)，在 Raspberry Pi 上安裝 .net。 從 Raspberry Pi (本機或 SSH) 上的 Bash 提示字元完成下列步驟：
    1. 執行下列命令以安裝 .NET：

        ```bash
        curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin
        ```

        > [!NOTE]
        > 這會安裝最新版本。 如果您需要特定版本，請新增 `--version <VERSION>` 至結尾，其中 `<VERSION>` 是特定的組建版本。

    1. 若要簡化路徑解析，請新增 `DOTNET_ROOT` 環境變數，並使用下列命令將 *dotnet* 目錄新增至 `$PATH` ：

        ```bash
        echo 'export DOTNET_ROOT=$HOME/.dotnet' >> ~/.bashrc
        echo 'export PATH=$PATH:$HOME/.dotnet' >> ~/.bashrc
        source ~/.bashrc
        ```

    1. 使用下列命令確認 .NET 安裝：

        ```dotnetcli
        dotnet --version
        ```

        確認顯示的版本符合您安裝的版本。

1. 根據開發環境，在開發電腦上發佈應用程式，如下所示。
    - 如果使用 **Visual Studio**，請將 [應用程式部署至本機資料夾](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019)。 在發佈之前，請在發行設定檔摘要中選取 [ **編輯** ]，然後選取 [ **設定** ] 索引標籤。確認 **部署模式** 設定為 [ *Framework 相依* ]，並將 [ **目標運行** 時間] 設定為 [ *可移植*]。
    - 如果使用 **.NET CLI**，請使用 [dotnet publish](../core/tools/dotnet-publish.md) 命令。 不需要額外的引數。

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. 從 Raspberry Pi (本機或 SSH) 的 Bash 提示字元中，執行應用程式。 若要這樣做，請將部署資料夾設定為目前的目錄，然後執行下列命令 (其中 *HelloWorld.dll* 是應用程式) 的進入點：

    ```dotnetcli
    dotnet HelloWorld.dll
    ```

## <a name="deploying-a-self-contained-app"></a>部署獨立式應用程式

若要將您的應用程式部署為獨立應用程式，請完成下列步驟：

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. 根據開發環境，在開發電腦上發佈應用程式，如下所示。
    - 如果使用 **Visual Studio**，請將 [應用程式部署至本機資料夾](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019)。 在發佈之前，請在發行設定檔摘要中選取 [ **編輯** ]，然後選取 [ **設定** ] 索引標籤。確認 **部署模式** 設定為 *獨立* ，而 **目標運行** 時間設定為 *linux-arm*。
    - 如果使用 **.NET CLI**，請使用 [dotnet publish](../core/tools/dotnet-publish.md) 命令搭配 `-r linux-arm` 引數：

        ```dotnetcli
        dotnet publish -r linux-arm
        ```

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. 從 Raspberry Pi (本機或 SSH) 的 Bash 提示字元中，執行應用程式。 若要這樣做，請將目前目錄設定為部署位置，然後完成下列步驟：
    1. 提供可執行檔 *execute* 許可權 (其中 `HelloWorld` 是可執行檔的名稱) 。

        ```bash
        chmod +x HelloWorld
        ```

    1. 執行可執行檔。

        ```bash
        ./HelloWorld
        ```

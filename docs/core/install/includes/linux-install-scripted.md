---
ms.openlocfilehash: 0d29407896145bc3b2ed8284c839ae8f2f0521b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602947"
---

[Dotnet-安裝腳本](../../tools/dotnet-install-script.md)會用於**SDK**的自動化和非系統管理員安裝。 您可以從 <https://dot.net/v1/dotnet-install.sh> 下載指令碼。

腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。 若要安裝目前的版本，這可能不是（LTS）版本，請使用 `-c Current` 參數。

```bash
./dotnet-install.sh -c Current
```

若要安裝 .NET Core 執行時間，而不是 SDK，請使用 `--runtime` 參數。

```bash
./dotnet-install.sh -c Current --runtime
```

您可以藉由變更參數來指定特定版本，以安裝特定版本 `-c` 。 下列命令會安裝 .NET Core SDK 3.1。

```bash
./dotnet-install.sh -c 3.1
```

如需詳細資訊，請參閱[dotnet-安裝腳本參考](../../tools/dotnet-install-script.md)。

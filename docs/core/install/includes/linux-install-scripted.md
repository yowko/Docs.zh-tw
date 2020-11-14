---
ms.openlocfilehash: 07dd58c314c826c426193b829ea1f64669fb888b
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594565"
---

[Dotnet 安裝腳本](../../tools/dotnet-install-script.md)用於自動化和非系統管理員安裝的 **SDK** 和 **運行** 時間。 您可以從 <https://dot.net/v1/dotnet-install.sh> 下載指令碼。

腳本預設會安裝最新的 SDK [長期支援 (LTS) ](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，也就是 .net 3.1。 若要安裝目前版本，這可能不是 (LTS) 版本，請使用 `-c Current` 參數。

```bash
./dotnet-install.sh -c Current
```

若要安裝 .NET 執行時間，而不是 SDK，請使用 `--runtime` 參數。

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

您可以藉由修改 `-c` 參數來指定特定版本，以安裝特定版本。 下列命令會安裝 .NET SDK 5.0。

```bash
./dotnet-install.sh -c 5.0
```

如需詳細資訊，請參閱 [dotnet-安裝腳本參考](../../tools/dotnet-install-script.md)。

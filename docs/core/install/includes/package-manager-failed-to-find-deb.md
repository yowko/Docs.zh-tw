---
ms.openlocfilehash: 7d398df060c031ae891218b82a2712d74f4c33b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602982"
---

如果您收到類似于**找不到封裝 {netcore}** 的錯誤訊息，請執行下列命令。

下列命令組中有兩個預留位置。

- `{dotnet-package}`\
這代表您要安裝的 .NET Core 套件，例如 `aspnetcore-runtime-3.1` 。 這會在 `sudo apt-get install` 下列命令中使用。

- `{os-version}`\
這代表您所在的 Linux 版本。 這會在 `wget` 下列命令中使用。

嘗試清除封裝清單：

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {dotnet-package}
```

如果無法解決問題，您可以使用下列命令來執行手動安裝：

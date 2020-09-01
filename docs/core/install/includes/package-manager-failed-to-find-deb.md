---
ms.openlocfilehash: 9d4c031eda291b0a8832c824789efdffe4084926
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132936"
---

如果您收到類似「 **找不到套件 {netcore-封裝}** 或 **某些套件無法安裝**」的錯誤訊息，請執行下列命令。

下列一組命令中有兩個預留位置。

- `{dotnet-package}`\
這代表您要安裝的 .NET Core 套件，例如 `aspnetcore-runtime-3.1` 。 這是在 `sudo apt-get install` 下列命令中使用。

- `{os-version}`\
這代表您所在的 Linux 版本。 這是在 `wget` 下列命令中使用。

首先，請嘗試清除套件清單：

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

然後，再次嘗試安裝 .NET Core。 如果無法運作，您可以使用下列命令來執行手動安裝：

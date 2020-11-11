---
ms.openlocfilehash: aba7b473af7685aa45f7e093a2f75311687593df
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506961"
---

如果您收到類似「 **找不到套件 {dotnet-封裝}** 或 **某些套件無法安裝** 」的錯誤訊息，請執行下列命令。

下列一組命令中有兩個預留位置。

- `{dotnet-package}`\
這代表您要安裝的 .NET 封裝，例如 `aspnetcore-runtime-3.1` 。 這會在下列命令中使用 `sudo apt-get install` 。

- `{os-version}`\
這代表您所在的 Linux 版本。 這是在 `wget` 下列命令中使用。

首先，請嘗試清除套件清單：

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

然後，再次嘗試安裝 .NET。 如果無法運作，您可以使用下列命令來執行手動安裝：

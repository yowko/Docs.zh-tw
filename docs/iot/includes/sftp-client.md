---
ms.openlocfilehash: 60e326af0d956ceb63b32e5d3ec2436fe09a7005
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "96586627"
---
[使用 SFTP 用戶端](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md)，將檔從開發電腦上的發佈位置複製到 Raspberry Pi 上的新資料夾。

例如，若要使用命令將檔案 `scp` 從開發電腦複製到您的 Raspberry Pi，請開啟命令提示字元並執行下列命令：

```console
scp -r /publish-location/* pi@raspberrypi:/home/pi/deployment-location/
```

其中：

- `-r`選項會指示 `scp` 以遞迴方式複製檔案。
- */publish-location/* 是您在上一個步驟中發佈到的資料夾。
- `pi@raspberypi` 是使用者和主機名稱的格式 `<username>@<hostname>` 。
- */home/pi/deployment-location/* 是 Raspberry pi 上的新資料夾。

> [!TIP]
> 最新版本的 Windows 具有 OpenSSH，其中包含 `scp` 預先安裝的。

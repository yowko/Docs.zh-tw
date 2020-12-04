---
ms.openlocfilehash: 60e326af0d956ceb63b32e5d3ec2436fe09a7005
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "96586627"
---
<span data-ttu-id="41b51-101">[使用 SFTP 用戶端](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md)，將檔從開發電腦上的發佈位置複製到 Raspberry Pi 上的新資料夾。</span><span class="sxs-lookup"><span data-stu-id="41b51-101">[Using an SFTP client](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md), copy the files from the publish location on the development computer to a new folder on the Raspberry Pi.</span></span>

<span data-ttu-id="41b51-102">例如，若要使用命令將檔案 `scp` 從開發電腦複製到您的 Raspberry Pi，請開啟命令提示字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="41b51-102">For example, to use the `scp` command to copy files from the development computer to your Raspberry Pi, open a command prompt and execute the following:</span></span>

```console
scp -r /publish-location/* pi@raspberrypi:/home/pi/deployment-location/
```

<span data-ttu-id="41b51-103">其中：</span><span class="sxs-lookup"><span data-stu-id="41b51-103">Where:</span></span>

- <span data-ttu-id="41b51-104">`-r`選項會指示 `scp` 以遞迴方式複製檔案。</span><span class="sxs-lookup"><span data-stu-id="41b51-104">The `-r` option instructs `scp` to copy files recursively.</span></span>
- <span data-ttu-id="41b51-105">*/publish-location/* 是您在上一個步驟中發佈到的資料夾。</span><span class="sxs-lookup"><span data-stu-id="41b51-105">*/publish-location/* is the folder you published to in the previous step.</span></span>
- <span data-ttu-id="41b51-106">`pi@raspberypi` 是使用者和主機名稱的格式 `<username>@<hostname>` 。</span><span class="sxs-lookup"><span data-stu-id="41b51-106">`pi@raspberypi` is the user and host names in the format `<username>@<hostname>`.</span></span>
- <span data-ttu-id="41b51-107">*/home/pi/deployment-location/* 是 Raspberry pi 上的新資料夾。</span><span class="sxs-lookup"><span data-stu-id="41b51-107">*/home/pi/deployment-location/* is the new folder on the Raspberry Pi.</span></span>

> [!TIP]
> <span data-ttu-id="41b51-108">最新版本的 Windows 具有 OpenSSH，其中包含 `scp` 預先安裝的。</span><span class="sxs-lookup"><span data-stu-id="41b51-108">Recent versions of Windows have OpenSSH, which includes `scp`, pre-installed.</span></span>

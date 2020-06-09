---
ms.openlocfilehash: 7d398df060c031ae891218b82a2712d74f4c33b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602982"
---

<span data-ttu-id="e0d47-101">如果您收到類似于**找不到封裝 {netcore}** 的錯誤訊息，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="e0d47-101">If you receive an error message similar to **Unable to locate package {netcore-package}**, run the following commands.</span></span>

<span data-ttu-id="e0d47-102">下列命令組中有兩個預留位置。</span><span class="sxs-lookup"><span data-stu-id="e0d47-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="e0d47-103">這代表您要安裝的 .NET Core 套件，例如 `aspnetcore-runtime-3.1` 。</span><span class="sxs-lookup"><span data-stu-id="e0d47-103">This represents the .NET Core package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="e0d47-104">這會在 `sudo apt-get install` 下列命令中使用。</span><span class="sxs-lookup"><span data-stu-id="e0d47-104">This is used in the `sudo apt-get install` command below.</span></span>

- `{os-version}`\
<span data-ttu-id="e0d47-105">這代表您所在的 Linux 版本。</span><span class="sxs-lookup"><span data-stu-id="e0d47-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="e0d47-106">這會在 `wget` 下列命令中使用。</span><span class="sxs-lookup"><span data-stu-id="e0d47-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="e0d47-107">嘗試清除封裝清單：</span><span class="sxs-lookup"><span data-stu-id="e0d47-107">Try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {dotnet-package}
```

<span data-ttu-id="e0d47-108">如果無法解決問題，您可以使用下列命令來執行手動安裝：</span><span class="sxs-lookup"><span data-stu-id="e0d47-108">If that doesn't work, you can run a manual install with the following commands:</span></span>

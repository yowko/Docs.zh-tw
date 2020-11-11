---
ms.openlocfilehash: aba7b473af7685aa45f7e093a2f75311687593df
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506961"
---

<span data-ttu-id="0e4ce-101">如果您收到類似「 **找不到套件 {dotnet-封裝}** 或 **某些套件無法安裝** 」的錯誤訊息，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="0e4ce-101">If you receive an error message similar to **Unable to locate package {dotnet-package}** or **Some packages could not be installed** , run the following commands.</span></span>

<span data-ttu-id="0e4ce-102">下列一組命令中有兩個預留位置。</span><span class="sxs-lookup"><span data-stu-id="0e4ce-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="0e4ce-103">這代表您要安裝的 .NET 封裝，例如 `aspnetcore-runtime-3.1` 。</span><span class="sxs-lookup"><span data-stu-id="0e4ce-103">This represents the .NET package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="0e4ce-104">這會在下列命令中使用 `sudo apt-get install` 。</span><span class="sxs-lookup"><span data-stu-id="0e4ce-104">This is used in the following `sudo apt-get install` command.</span></span>

- `{os-version}`\
<span data-ttu-id="0e4ce-105">這代表您所在的 Linux 版本。</span><span class="sxs-lookup"><span data-stu-id="0e4ce-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="0e4ce-106">這是在 `wget` 下列命令中使用。</span><span class="sxs-lookup"><span data-stu-id="0e4ce-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="0e4ce-107">首先，請嘗試清除套件清單：</span><span class="sxs-lookup"><span data-stu-id="0e4ce-107">First, try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

<span data-ttu-id="0e4ce-108">然後，再次嘗試安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="0e4ce-108">Then, try to install .NET again.</span></span> <span data-ttu-id="0e4ce-109">如果無法運作，您可以使用下列命令來執行手動安裝：</span><span class="sxs-lookup"><span data-stu-id="0e4ce-109">If that doesn't work, you can run a manual install with the following commands:</span></span>

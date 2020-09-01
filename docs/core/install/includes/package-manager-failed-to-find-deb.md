---
ms.openlocfilehash: 9d4c031eda291b0a8832c824789efdffe4084926
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132936"
---

<span data-ttu-id="38542-101">如果您收到類似「 **找不到套件 {netcore-封裝}** 或 **某些套件無法安裝**」的錯誤訊息，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="38542-101">If you receive an error message similar to **Unable to locate package {netcore-package}** or **Some packages could not be installed**, run the following commands.</span></span>

<span data-ttu-id="38542-102">下列一組命令中有兩個預留位置。</span><span class="sxs-lookup"><span data-stu-id="38542-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="38542-103">這代表您要安裝的 .NET Core 套件，例如 `aspnetcore-runtime-3.1` 。</span><span class="sxs-lookup"><span data-stu-id="38542-103">This represents the .NET Core package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="38542-104">這是在 `sudo apt-get install` 下列命令中使用。</span><span class="sxs-lookup"><span data-stu-id="38542-104">This is used in the `sudo apt-get install` command below.</span></span>

- `{os-version}`\
<span data-ttu-id="38542-105">這代表您所在的 Linux 版本。</span><span class="sxs-lookup"><span data-stu-id="38542-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="38542-106">這是在 `wget` 下列命令中使用。</span><span class="sxs-lookup"><span data-stu-id="38542-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="38542-107">首先，請嘗試清除套件清單：</span><span class="sxs-lookup"><span data-stu-id="38542-107">First, try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

<span data-ttu-id="38542-108">然後，再次嘗試安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="38542-108">Then, try to install .NET Core again.</span></span> <span data-ttu-id="38542-109">如果無法運作，您可以使用下列命令來執行手動安裝：</span><span class="sxs-lookup"><span data-stu-id="38542-109">If that doesn't work, you can run a manual install with the following commands:</span></span>

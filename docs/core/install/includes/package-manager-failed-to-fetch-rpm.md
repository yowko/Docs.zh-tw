---
ms.openlocfilehash: 8c05af045d2d9666b20f36e36c68cc853f906eae
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506847"
---

<span data-ttu-id="c180e-101">安裝 .NET 封裝時，您可能會看到類似的錯誤 `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'` 。</span><span class="sxs-lookup"><span data-stu-id="c180e-101">While installing the .NET package, you may see an error similar to `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`.</span></span> <span data-ttu-id="c180e-102">一般來說，此錯誤表示 .NET 的套件摘要正以較新的套件版本進行升級，您應該稍後再試一次。</span><span class="sxs-lookup"><span data-stu-id="c180e-102">Generally speaking, this error means that the package feed for .NET is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="c180e-103">在升級期間，套件摘要不能使用超過2小時。</span><span class="sxs-lookup"><span data-stu-id="c180e-103">During an upgrade, the package feed should not be unavailable for more than 2 hours.</span></span> <span data-ttu-id="c180e-104">如果您持續收到超過2小時的錯誤，請在中提出問題 <https://github.com/dotnet/core/issues> 。</span><span class="sxs-lookup"><span data-stu-id="c180e-104">If you continually receive this error for more than 2 hours, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>

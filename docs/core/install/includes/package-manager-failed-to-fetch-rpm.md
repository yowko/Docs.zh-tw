---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920724"
---

<span data-ttu-id="06c30-101">安裝 .NET Core 套件時，您可能會看到類似 `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`的錯誤。</span><span class="sxs-lookup"><span data-stu-id="06c30-101">While installing the .NET Core package, you may see an error similar to `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`.</span></span> <span data-ttu-id="06c30-102">一般來說，此錯誤表示 .NET Core 的套件摘要正以較新的封裝版本進行升級，您應該稍後再試一次。</span><span class="sxs-lookup"><span data-stu-id="06c30-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="06c30-103">在升級期間，套件摘要不能使用超過2小時。</span><span class="sxs-lookup"><span data-stu-id="06c30-103">During an upgrade, the package feed should not be unavailable for more than 2 hours.</span></span> <span data-ttu-id="06c30-104">如果您持續收到此錯誤超過2小時，請在 <https://github.com/dotnet/core/issues>提出問題。</span><span class="sxs-lookup"><span data-stu-id="06c30-104">If you continually receive this error for more than 2 hours, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>

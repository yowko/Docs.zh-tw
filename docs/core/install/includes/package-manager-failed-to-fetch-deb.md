---
ms.openlocfilehash: 3bb59ba23214f67100d3a78bb689c941b2d187e6
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506962"
---

<span data-ttu-id="a0c11-101">安裝 .NET 封裝時，您可能會看到類似的錯誤 `Failed to fetch ... File has unexpected size ... Mirror sync in progress?` 。</span><span class="sxs-lookup"><span data-stu-id="a0c11-101">While installing the .NET package, you may see an error similar to `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span></span> <span data-ttu-id="a0c11-102">此錯誤可能表示 .NET 的套件摘要正以較新的套件版本進行升級，您應該稍後再試一次。</span><span class="sxs-lookup"><span data-stu-id="a0c11-102">This error could mean that the package feed for .NET is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="a0c11-103">在升級期間，套件摘要不能使用超過30分鐘。</span><span class="sxs-lookup"><span data-stu-id="a0c11-103">During an upgrade, the package feed shouldn't be unavailable for more than 30 minutes.</span></span> <span data-ttu-id="a0c11-104">如果您持續收到超過30分鐘的這個錯誤，請在中提出問題 <https://github.com/dotnet/core/issues> 。</span><span class="sxs-lookup"><span data-stu-id="a0c11-104">If you continually receive this error for more than 30 minutes, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>

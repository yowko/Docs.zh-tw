---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920724"
---

<span data-ttu-id="43b44-101">安裝 .NET Core 包時，您可能會看到類似于`signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`的錯誤。</span><span class="sxs-lookup"><span data-stu-id="43b44-101">While installing the .NET Core package, you may see an error similar to `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`.</span></span> <span data-ttu-id="43b44-102">通常，此錯誤意味著 .NET Core 的包源正在使用較新的包版本進行升級，以後應重試。</span><span class="sxs-lookup"><span data-stu-id="43b44-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="43b44-103">在升級期間，包源不應在 2 小時內不可用。</span><span class="sxs-lookup"><span data-stu-id="43b44-103">During an upgrade, the package feed should not be unavailable for more than 2 hours.</span></span> <span data-ttu-id="43b44-104">如果您連續收到此錯誤超過 2 小時，請在 上<https://github.com/dotnet/core/issues>提交問題。</span><span class="sxs-lookup"><span data-stu-id="43b44-104">If you continually receive this error for more than 2 hours, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>

---
ms.openlocfilehash: 98ec28fc1f91512a61f64a36f7749379e864fea1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920637"
---

<span data-ttu-id="8a1ee-101">安裝 .NET Core 包時，您可能會看到類似于`Failed to fetch ... File has unexpected size ... Mirror sync in progress?`的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8a1ee-101">While installing the .NET Core package, you may see an error similar to `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span></span> <span data-ttu-id="8a1ee-102">通常，此錯誤意味著 .NET Core 的包源正在使用較新的包版本進行升級，以後應重試。</span><span class="sxs-lookup"><span data-stu-id="8a1ee-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="8a1ee-103">在升級期間，包源不應在 30 分鐘內不可用。</span><span class="sxs-lookup"><span data-stu-id="8a1ee-103">During an upgrade, the package feed should not be unavailable for more than 30 minutes.</span></span> <span data-ttu-id="8a1ee-104">如果您連續收到此錯誤超過 30 分鐘，請在 上<https://github.com/dotnet/core/issues>提交問題。</span><span class="sxs-lookup"><span data-stu-id="8a1ee-104">If you continually receive this error for more than 30 minutes, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>

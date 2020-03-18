---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920724"
---

安裝 .NET Core 包時，您可能會看到類似于`signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`的錯誤。 通常，此錯誤意味著 .NET Core 的包源正在使用較新的包版本進行升級，以後應重試。 在升級期間，包源不應在 2 小時內不可用。 如果您連續收到此錯誤超過 2 小時，請在 上<https://github.com/dotnet/core/issues>提交問題。

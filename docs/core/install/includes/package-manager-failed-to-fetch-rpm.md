---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920724"
---

安裝 .NET Core 封裝時，您可能會看到類似的錯誤 `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'` 。 一般來說，此錯誤表示 .NET Core 的套件摘要正以較新的套件版本進行升級，您應該稍後再試一次。 在升級期間，套件摘要不能使用超過2小時。 如果您持續收到超過2小時的錯誤，請在中提出問題 <https://github.com/dotnet/core/issues> 。

---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920724"
---

安裝 .NET Core 套件時，您可能會看到類似 `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`的錯誤。 一般來說，此錯誤表示 .NET Core 的套件摘要正以較新的封裝版本進行升級，您應該稍後再試一次。 在升級期間，套件摘要不能使用超過2小時。 如果您持續收到此錯誤超過2小時，請在 <https://github.com/dotnet/core/issues>提出問題。

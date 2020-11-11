---
ms.openlocfilehash: 8c05af045d2d9666b20f36e36c68cc853f906eae
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506847"
---

安裝 .NET 封裝時，您可能會看到類似的錯誤 `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'` 。 一般來說，此錯誤表示 .NET 的套件摘要正以較新的套件版本進行升級，您應該稍後再試一次。 在升級期間，套件摘要不能使用超過2小時。 如果您持續收到超過2小時的錯誤，請在中提出問題 <https://github.com/dotnet/core/issues> 。

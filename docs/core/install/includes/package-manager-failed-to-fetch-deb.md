---
ms.openlocfilehash: 15418d1ac3ade6a0fa35ca61a02134e20af1baea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602975"
---

安裝 .NET Core 封裝時，您可能會看到類似的錯誤 `Failed to fetch ... File has unexpected size ... Mirror sync in progress?` 。 此錯誤可能表示 .NET Core 的套件摘要正以較新的套件版本進行升級，您應該稍後再試一次。 在升級期間，套件摘要不能使用超過30分鐘。 如果您持續收到超過30分鐘的這個錯誤，請在中提出問題 <https://github.com/dotnet/core/issues> 。

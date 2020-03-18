---
ms.openlocfilehash: 98ec28fc1f91512a61f64a36f7749379e864fea1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920637"
---

安裝 .NET Core 包時，您可能會看到類似于`Failed to fetch ... File has unexpected size ... Mirror sync in progress?`的錯誤。 通常，此錯誤意味著 .NET Core 的包源正在使用較新的包版本進行升級，以後應重試。 在升級期間，包源不應在 30 分鐘內不可用。 如果您連續收到此錯誤超過 30 分鐘，請在 上<https://github.com/dotnet/core/issues>提交問題。

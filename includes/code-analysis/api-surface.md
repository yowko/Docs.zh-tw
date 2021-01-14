---
ms.openlocfilehash: bf7ea8a36b9c36d82b4c00ada890829bf4c2c024
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "97700852"
---
### <a name="include-specific-api-surfaces"></a>包含特定 API 表面

您可以根據其存取範圍，設定程式碼基底的哪些部分來執行此規則。 例如，若要指定規則只能針對非公用 API 介面執行，請將下列機碼值組新增至專案中的 *editorconfig* 檔案：

```ini
dotnet_code_quality.CAXXXX.api_surface = private, internal
```

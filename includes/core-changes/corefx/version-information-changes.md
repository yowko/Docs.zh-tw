---
ms.openlocfilehash: 5bed2d1d4eda4a4c577f05f614a71aa9180998a7
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182050"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>報告版本的 Api 現在會報告產品，而不是檔案版本

許多在 .NET Core 中傳回版本的 Api 現在都會傳回產品版本，而不是檔案版本。

#### <a name="change-description"></a>變更描述

在 .net core 2.2 和舊版中，.net core 元件<xref:System.Environment.Version?displayProperty=nameWithType>（ <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>例如、和）的 [檔案屬性] 對話方塊等方法會反映檔案版本。 從 .NET Core 3.0 開始，它們會反映產品版本。 

下圖說明 .NET Core 2.2 （左側）和 .NET Core 3.0 （位於右邊）的*system.webserver*元件版本資訊差異，如**Windows Explorer** [檔案屬性] 對話方塊所顯示。

![產品版本資訊的差異](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

無。 這種變更應該可以直覺而不是簡直遲鈍進行版本偵測。

#### <a name="category"></a>分類

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`


-->
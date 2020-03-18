---
ms.openlocfilehash: 5612ebce67946e22aaeeba861115ce4f8967e1f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344437"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>報表版本的 API 現在報告產品，而不是檔版本

返回 .NET Core 中版本的許多 API 現在返回產品版本，而不是檔版本。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 和早期版本中<xref:System.Environment.Version?displayProperty=nameWithType>，<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>方法（如 .NET Core 程式集的檔案屬性對話方塊）反映檔版本。 從 .NET Core 3.0 開始，它們反映了產品版本。

下圖說明瞭 Windows**資源管理器**檔案屬性對話方塊顯示的*System.Runtime.dll*.NET Core 2.2（左側）和 .NET Core 3.0（右側）的版本資訊差異。

![產品版本資訊的差異](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

無。 此更改應使版本檢測直觀，而不是過時。

#### <a name="category"></a>類別

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->

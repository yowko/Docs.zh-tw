---
ms.openlocfilehash: 1580c8c8b7bdad91656f494537230293dbaaf93b
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021624"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>報表版本的 API 現在報告產品,而不是檔案版本

返回 .NET Core 中版本的許多 API 現在傳回產品版本,而不是檔版本。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2<xref:System.Environment.Version?displayProperty=nameWithType>和<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>早期版本中, 方法(如 .NET Core 程式集的檔屬性對話框)反映檔版本。 從 .NET Core 3.0 開始,它們反映了產品版本。

下圖說明了 Windows**資源管理器**文件屬性對話*System.Runtime.dll*框顯示的 .NET Core 2.2(左側)和 .NET Core 3.0(右側)的版本資訊差異。

![產品版本資訊的差異](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

無。 此更改應使版本檢測直觀,而不是過時。

#### <a name="category"></a>類別

核心 .NET 函式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->

---
ms.openlocfilehash: bb264e406c6604c3606e564d99018eda0f9e8d89
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721049"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>報告版本的 Api 現在會報告產品，而不是檔案版本

許多傳回 .NET Core 版本的 Api 現在會傳回產品版本，而不是檔案版本。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 和舊版中， <xref:System.Environment.Version?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> .net core 元件（例如、和）的 [檔案屬性] 對話方塊等方法會反映檔案版本。 從 .NET Core 3.0 開始，它們會反映產品版本。

下圖說明 .NET Core 2.2 （左側）和 .NET Core 3.0 （位於右邊）的*system.webserver*元件版本資訊差異，如**Windows Explorer** [檔案屬性] 對話方塊所顯示。

![產品版本資訊的差異](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

無。 這種變更應該可以直覺而不是簡直遲鈍進行版本偵測。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->

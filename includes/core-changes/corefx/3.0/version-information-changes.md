---
ms.openlocfilehash: bb264e406c6604c3606e564d99018eda0f9e8d89
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032038"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>報表版本現在會回報產品而非檔案版本的 Api

在 .NET Core 中傳回版本的許多 Api 現在都會傳回產品版本，而不是檔案版本。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 和舊版中， <xref:System.Environment.Version?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> .net core 元件的方法（如、和）和檔案屬性對話方塊會反映檔案版本。 從 .NET Core 3.0 開始，它們會反映產品版本。

下圖說明 **)** [檔案屬性] 對話方塊所顯示的左邊) 和 .net core 3.0 (上的 .net core (2.2 *System.Runtime.dll* 元件的版本資訊差異。

![產品版本資訊的差異](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

無。 這種變更應該可讓您以直覺而非遲鈍的形式進行版本偵測。

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

---
ms.openlocfilehash: d207a937917da78f6b902ad8ca4f02fa9a46c2e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116345"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Microsoft 中的類型.VisualBasic.MyServices 命名空間不可用

命名空間中<xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>的類型不可用。

#### <a name="version-introduced"></a>介紹的版本

.NET 核心 3.0 預覽 8

#### <a name="change-description"></a>變更描述

命名空間中<xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>的類型在某些 .NET Core 3.0 預覽版本中可用。 它們不再可用，從 .NET 核心 3.0 預覽 9 開始。

已刪除這些類型，以避免不必要的程式集依賴關係或後續版本中的中斷更改。

#### <a name="recommended-action"></a>建議的動作

如果您的代碼取決於**Microsoft.VisualBasic.MyServices**類型及其成員的使用，則 .NET 類庫中有相應的類型和成員。 以下是**Microsoft.VisualBasic.MyServices**的映射，其等效的 .NET 類庫類型：

|微軟.視覺基礎.我的服務類型|.NET 類庫類型|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType>對於 WPF<xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType>應用程式，用於 Windows 表單應用程式|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|命名空間中<xref:System.IO>的類型|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|命名空間中的<xref:Microsoft.Win32>註冊表相關類型|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>類別

Visual Basic

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->

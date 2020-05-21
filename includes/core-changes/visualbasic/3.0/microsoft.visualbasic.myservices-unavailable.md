---
ms.openlocfilehash: acb8ed44b7d18b257731e32339f087c8fe5fdd4a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721309"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>MyServices 命名空間中的類型無法使用

命名空間中的類型 <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> 無法使用。

#### <a name="version-introduced"></a>引進的版本

.NET Core 3.0 Preview 8

#### <a name="change-description"></a>變更描述

命名空間中的類型 <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> 可在某些 .Net Core 3.0 預覽版本中使用。 從 .NET Core 3.0 Preview 9 開始就不再提供這些功能。

已移除類型，以避免不必要的元件相依性或後續版本中的重大變更。

#### <a name="recommended-action"></a>建議的動作

如果您的程式碼相依于**MyServices**類型及其成員，則 .net 類別庫中會有對應的類型和成員。 以下是**MyServices**類型對應到其對等 .net 類別庫類型的對應：

|MyServices 類型|.NET 類別庫類型|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType>針對 WPF 應用程式， <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> 適用于 Windows Forms 應用程式|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|命名空間中的類型 <xref:System.IO>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|命名空間中與登錄相關的類型 <xref:Microsoft.Win32>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>類別

Visual Basic

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->

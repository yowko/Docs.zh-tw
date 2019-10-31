---
ms.openlocfilehash: 58e65bae1593f23945a971b896a1db4a929b4587
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198372"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>MyServices 命名空間中的類型無法使用

<xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> 命名空間中的類型無法使用。

#### <a name="version-introduced"></a>引進的版本

.NET Core 3.0 Preview 8

#### <a name="change-description"></a>變更描述

在某些 .NET Core 3.0 Preview 版本中，可以使用 <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> 命名空間中的類型。 從 .NET Core 3.0 Preview 9 開始就不再提供這些功能。

已移除類型，以避免不必要的元件相依性或後續版本中的重大變更。

#### <a name="recommended-action"></a>建議的動作

如果您的程式碼相依于**MyServices**類型及其成員，則 .net 類別庫中會有對應的類型和成員。 以下是**MyServices**類型對應到其對等 .net 類別庫類型的對應：

|MyServices 類型|.NET 類別庫類型|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|適用于 WPF 應用程式的 <xref:System.Windows.Clipboard?displayProperty=nameWithType>，<xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> 適用于 Windows Forms 應用程式|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<xref:System.IO> 命名空間中的類型|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<xref:Microsoft.Win32> 命名空間中的登錄相關類型|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >


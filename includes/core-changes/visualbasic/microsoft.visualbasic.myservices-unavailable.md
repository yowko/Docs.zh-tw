---
ms.openlocfilehash: d61e4da187b3ede5e49fa80903d6e4c3b40578b9
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216300"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>MyServices 命名空間中的類型無法使用

<xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>命名空間中的類型無法使用。

#### <a name="version-introduced"></a>引進的版本

.NET Core 3.0 Preview 8

#### <a name="details"></a>詳細資料

<xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>命名空間中的類型可在某些 .net Core 3.0 預覽版本中使用。 從 .NET Core 3.0 Preview 9 開始就不再提供這些功能。

已移除類型，以避免不必要的元件相依性或後續版本中的重大變更。
 
#### <a name="recommended-action"></a>建議的動作

如果您的程式碼相依于**MyServices**類型及其成員，則 .net 類別庫中會有對應的類型和成員。 以下是**MyServices**類型對應到其對等 .net 類別庫類型的對應：

|MyServices 類型|.NET 類別庫類型|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType>針對 WPF 應用程式<xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> ，適用于 Windows Forms 應用程式| 
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|命名空間中<xref:System.IO>的類型|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<xref:Microsoft.Win32>命名空間中與登錄相關的類型|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>分類

Visual Basic

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >


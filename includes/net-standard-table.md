---
ms.openlocfilehash: 9e95db8a1530fabd30b5344c87728b9210c0ad69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "74802830"
---
| .NET Standard              | [1.0]  | [1.1]  | [1.2] | [1.3] | [1.4] | [1.5]              | [1.6]              | [2.0]               | [2.1] |
|----------------------------|--------|--------|-------|-------|-------|--------------------|--------------------|---------------------|---------------------
| .NET Core                  | 1.0    | 1.0    | 1.0   | 1.0   | 1.0   | 1.0                | 1.0                | 2.0                 | 3.0 |
| .NET Framework <sup>1</sup>| 4.5    | 4.5    | 4.5.1 | 4.6   | 4.6.1 | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup>  | 不適用<sup>3</sup> |
| Mono                       | 4.6    | 4.6    | 4.6   | 4.6   | 4.6   | 4.6                | 4.6                | 5.4                 | 6.4 |
| Xamarin.iOS                | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0               | 10.0               | 10.14               | 12.16 |
| Xamarin.Mac                | 3.0    | 3.0    | 3.0   | 3.0   | 3.0   | 3.0                | 3.0                | 3.8                 | 5.16 |
| Xamarin.Android            | 7.0    | 7.0    | 7.0   | 7.0   | 7.0   | 7.0                | 7.0                | 8.0                 | 10.0 |
| 通用 Windows 平台 | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0.16299         | 10.0.16299         | 10.0.16299          | TBD |
| Unity                      | 2018.1 | 2018.1 | 2018.1| 2018.1| 2018.1| 2018.1             |  2018.1            | 2018.1              | TBD |

<sup>1 為 .NET 框架列出的版本適用于 .NET Core 2.0 SDK 和該工具的更高版本。舊版本對 .NET 標準 1.5 及更高版本使用不同的映射。如果您無法升級到 Visual Studio 2017 或更高版本，則可以[下載適用于 2015 年 Visual Studio 的 .NET 核心工具](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)的工具。</sup>

<sup>2 此處列出的版本表示 NuGet 用於確定給定 .NET 標準庫是否適用的規則。雖然 NuGet 認為 .NET 框架 4.6.1 支援 .NET 標準 1.5 到 2.0，但使用 .NET 標準庫存在幾個問題，這些庫是為這些版本從 .NET Framework 4.6.1 專案中構建的。對於需要使用此類庫的 .NET Framework 專案，我們建議您將專案升級到目標 .NET Framework 4.7.2 或更高版本。</sup>

<sup>3 .NET 框架不支援 .NET 標準 2.1 或更高版本。有關詳細資訊，請參閱[.NET 標準 2.1](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-1/)的公告。</sup>

- 資料行代表 .NET Standard 版本。 每個標題儲存格都是一個文件連結，該文件說明在該 .NET Standard 版本中新增了哪些 API。
- 資料列代表不同的 .NET 實作。
- 每個資料格中的版本號碼分別表示以該 .NET Standard 版本為目標所需的「最低」** 實作版本。
- 若為互動式資料表，請參閱 [.NET Standard 版本](https://dotnet.microsoft.com/platform/dotnet-standard#versions)。

[1.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.0.md
[1.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.1.md
[1.2]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.2.md
[1.3]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.3.md
[1.4]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.4.md
[1.5]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.5.md
[1.6]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.6.md
[2.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md
[2.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.1.md

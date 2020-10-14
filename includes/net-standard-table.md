---
ms.openlocfilehash: 72b371dc2a6475efa2e0353f87dbdfa96c4c7c0e
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050388"
---
| .NET Standard              | [1.0]  | [1.1]  | [1.2] | [1.3] | [1.4] | [1.5]              | [1.6]              | [2.0]               | [2.1] |
|----------------------------|--------|--------|-------|-------|-------|--------------------|--------------------|---------------------|---------------------
| .NET Core 和 .NET 5       | 1.0    | 1.0    | 1.0   | 1.0   | 1.0   | 1.0                | 1.0                | 2.0                 | 3.0 |
| .NET Framework <sup>1</sup>| 4.5    | 4.5    | 4.5.1 | 4.6   | 4.6.1 | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup>  | 不適用<sup>3</sup> |
| Mono                       | 4.6    | 4.6    | 4.6   | 4.6   | 4.6   | 4.6                | 4.6                | 5.4                 | 6.4 |
| Xamarin.iOS                | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0               | 10.0               | 10.14               | 12.16 |
| Xamarin.Mac                | 3.0    | 3.0    | 3.0   | 3.0   | 3.0   | 3.0                | 3.0                | 3.8                 | 5.16 |
| Xamarin.Android            | 7.0    | 7.0    | 7.0   | 7.0   | 7.0   | 7.0                | 7.0                | 8.0                 | 10.0 |
| 通用 Windows 平台 | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0.16299         | 10.0.16299         | 10.0.16299          | TBD |
| Unity                      | 2018.1 | 2018.1 | 2018.1| 2018.1| 2018.1| 2018.1             |  2018.1            | 2018.1              | TBD |

<sup>1針對 .NET Framework 所列出的版本適用于 .NET Core 2.0 SDK 和更新版本的工具。舊版使用不同的對應來 .NET Standard 1.5 和更新版本。如果您無法升級至 Visual Studio 2017 或更新版本，您可以下載適用于 [Visual Studio 2015 的 .Net Core 工具](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md) 的工具。</sup>

<sup>2列出的版本代表 NuGet 用來判斷指定 .NET Standard 程式庫是否適用的規則。雖然 NuGet 會將 .NET Framework 4.6.1 視為支援 .NET Standard 1.5 至2.0，但使用從 .NET Framework 4.6.1 專案針對這些版本所建立的 .NET Standard 程式庫有幾個問題。對於需要使用這類程式庫 .NET Framework 專案，建議您將專案升級為以 .NET Framework 4.7.2 或更高版本為目標。</sup>

<sup>3 .NET Framework 不支援 .NET Standard 2.1。如需詳細資訊，請參閱 [.NET Standard 2.1 的公告](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-1/)。</sup>

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

---
title: .NET 標準中的新增功能
description: 本文摘要說明 .NET Standard 的每個新版本中的新功能和增強功能。
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 28d6a3546e08bbc3a7d4a26f08ba9cc5e16a901b
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438208"
---
# <a name="whats-new-in-net-standard"></a>.NET 標準中的新增功能

.NET 標準是一種正式規範,它定義了一組版本化的 API,這些 API 必須在符合該版本的標準的 .NET 實現上可用。 .NET 標準針對庫開發人員。 以 .NET Standard 版本為目標的程式庫可以用於任何支援該標準的版本之 .NET Framework、.NET Core 或 Xamarin 實作。

.NET 標準包含在 .NET 核心 SDK 以及 Visual Studio 中,當您選擇 .NET 核心工作負載時。

## <a name="supported-net-implementations"></a>支援的 .NET 實作

.NET 標準 2.0 由以下 .NET 實現提供支援:

- .NET Core 2.0 或更新版本
- .NET Framework 4.6.1 或更新版本
- Mono 5.4 或更新版本
- Xamarin.iOS 10.14 或更新版本
- Xamarin.Mac 3.8 或更新版本
- Xamarin.Android 8.0 或更新版本
- 通用 Windows 平台 10.0.16299 或更新版本

## <a name="whats-new-in-net-standard-20"></a>.NET 標準 2.0 中的新增功能

.NET 標準 2.0 包括以下新功能:

### <a name="a-vastly-expanded-set-of-apis"></a>一組大幅擴充的 API

通過版本 1.6,.NET 標準包含相對較小的 API 子集。 其中排除那些經常用於 .NET Framework 或 Xamarin 的許多 API。 這讓開發變得複雜，因為當開發人員開發以多個 .NET 實作為目標的應用程式和程式庫時，他們必須尋找熟悉的 API 之合適替代方案。 .NET 標準 2.0 通過添加超過 20,000 個 API 來解決此限制,API 比標準的早期版本 .NET 標準 1.6 中可用。 有關已添加到 .NET 標準 2.0 的 API 清單,請參閱[.NET 標準 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md)。

一些新增到 .NET Standard 2.0 中 <xref:System> 命名空間的項目包括：

- <xref:System.AppDomain> 類別的支援。
- 從 <xref:System.Array> 類別中其他成員使用陣列的更好之支援。
- 從 <xref:System.Attribute> 類別中其他成員使用屬性的更好之支援。
- <xref:System.DateTime> 值的更好之行事曆支援和其他格式選項。
- 其他 <xref:System.Decimal> 四捨五入功能。
- <xref:System.Environment> 類別中的其他功能。
- 增強透過 <xref:System.GC> 類別的記憶體回收行程的控制。
- 增強 <xref:System.String> 類別中字串比較、列舉和正規化的支援。
- 支援日光節約調整和 <xref:System.TimeZoneInfo.AdjustmentRule> 與 <xref:System.TimeZoneInfo.TransitionTime> 類別中的轉換時間。
- 大幅增強 <xref:System.Type> 類別中的功能。
- 藉由新增包含 <xref:System.Runtime.Serialization.SerializationInfo> 和 <xref:System.Runtime.Serialization.StreamingContext> 參數的例外狀況建構函式，提供例外狀況物件還原序列化更好的支援。

### <a name="support-for-net-framework-libraries"></a>針對 .NET Framework 程式庫的支援

絕大多數庫都以 .NET 框架為目標,而不是 .NET 標準。 但是,這些庫中的大多數調用都是 .NET 標準 2.0 中包含的 API。 從 .NET 標準 2.0 開始,可以使用[相容性希姆](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification)從 .NET 標準庫訪問 .NET 框架庫。 此相容性層級對開發人員是透明的，您不需要執行任何動作就能利用.NET Framework 程式庫。

單一要求是 .NET 框架類庫調用的 API 必須包含在 .NET 標準 2.0 中。

### <a name="support-for-visual-basic"></a>Visual Basic 的支援

您現在可以在 Visual Basic 中開發 .NET Standard 程式庫。 Visual Studio 2019 和 Visual Studio 2017 版本 15.3 或更高版本安裝了 .NET 核心工作負載,包括 .NET 標準類庫範本。 對於使用其他開發工具和環境的 Visual Basic 開發人員，您可以使用 [dotnet new](../../core/tools/dotnet-new.md) 命令來建立 .NET Standard 程式庫專案。 如需詳細資訊，請參閱 [.NET Standard 程式庫的工具支援](#tooling-support-for-net-standard-libraries)。

### <a name="tooling-support-for-net-standard-libraries"></a>.NET Standard 程式庫的工具支援

隨著 .NET Core 2.0 和 .NET 標準 2.0 的發佈,Visual Studio 2017 和[.NET 核心 CLI](../../core/tools/index.md)都包含了創建 .NET 標準庫的工具支援。

如果安裝具有 **.NET Core 跨平台開發工作負載的**Visual Studio,則可以使用專案範本建立 .NET 標準 2.0 庫專案,如下圖所示:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C#](#tab/csharp)

![新增 .NET Standard 程式庫專案](./media/std-project-cs.png)

如果使用 .NET Core CLI,以下[dotnet 新](../../core/tools/dotnet-new.md)指令將建立一個面向 .NET 標準 2.0 的類別庫專案:

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

![新增 .NET Standard 程式庫專案](./media/std-project-vb.png)

如果使用 .NET Core CLI,以下[dotnet 新](../../core/tools/dotnet-new.md)指令將建立一個面向 .NET 標準 2.0 的類別庫專案:

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>另請參閱

- [.NET Standard](../net-standard.md)
- [.NET Standard 簡介](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)

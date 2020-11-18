---
title: .NET Standard 的新功能
description: 本文摘要說明 .NET Standard 的每個新版本中的新功能和增強功能。
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.prod: dotnet-whatsnew
ms.openlocfilehash: 299477a7375381fa7f8064562e2a68e221944a05
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817170"
---
# <a name="whats-new-in-net-standard"></a>.NET Standard 的新功能

.NET Standard 是正式規格，可定義一組已建立版本的 Api，這些 Api 必須可在符合該標準版本的 .NET 執行上使用。 .NET Standard 是以程式庫開發人員為目標。 以 .NET Standard 版本為目標的程式庫可以用於任何支援該標準的版本之 .NET Framework、.NET Core 或 Xamarin 實作。

當您選取 .NET Core 工作負載時，.NET Standard 會隨附于 .NET Core SDK 和 Visual Studio。

## <a name="supported-net-implementations"></a>支援的 .NET 實作

下列 .NET 部署支援 .NET Standard 2.0：

- .NET Core 2.0 或更新版本
- .NET Framework 4.6.1 或更新版本
- Mono 5.4 或更新版本
- Xamarin.iOS 10.14 或更新版本
- Xamarin.Mac 3.8 或更新版本
- Xamarin.Android 8.0 或更新版本
- 通用 Windows 平台 10.0.16299 或更新版本

## <a name="whats-new-in-net-standard-20"></a>.NET Standard 2.0 的新功能

.NET Standard 2.0 包含下列新功能：

### <a name="a-vastly-expanded-set-of-apis"></a>一組大幅擴充的 API

在1.6 版中，.NET Standard 包含相對較小的 Api 子集。 其中所排除的許多 Api 通常用於 .NET Framework 或 Xamarin 中。 這讓開發變得複雜，因為當開發人員開發以多個 .NET 實作為目標的應用程式和程式庫時，他們必須尋找熟悉的 API 之合適替代方案。 .NET Standard 2.0 藉由新增超過20000個 Api （比舊版標準的 .NET Standard 1.6）來解決這項限制。 如需已新增至 .NET Standard 2.0 的 Api 清單，請參閱 [.NET Standard 2.0 與 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md)。

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

許多程式庫的目標都是 .NET Framework 而不是 .NET Standard。 不過，這些程式庫中的大部分呼叫都是包含在 .NET Standard 2.0 中的 Api。 從 .NET Standard 2.0 開始，您可以使用 [相容性填充碼](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification)從 .NET Standard 程式庫存取 .NET Framework 程式庫。 此相容性層級對開發人員是透明的，您不需要執行任何動作就能利用.NET Framework 程式庫。

單一需求是 .NET Framework 類別庫所呼叫的 Api 必須包含在 .NET Standard 2.0 中。

### <a name="support-for-visual-basic"></a>Visual Basic 的支援

您現在可以在 Visual Basic 中開發 .NET Standard 程式庫。 已安裝 .NET Core 工作負載的 Visual Studio 2019 和 Visual Studio 2017 15.3 版或更新版本，包括 .NET Standard 類別庫範本。 對於使用其他開發工具和環境的 Visual Basic 開發人員，您可以使用 [dotnet new](../../core/tools/dotnet-new.md) 命令來建立 .NET Standard 程式庫專案。 如需詳細資訊，請參閱 [.NET Standard 程式庫的工具支援](#tooling-support-for-net-standard-libraries)。

### <a name="tooling-support-for-net-standard-libraries"></a>.NET Standard 程式庫的工具支援

隨著 .NET Core 2.0 和 .NET Standard 2.0 的發行，Visual Studio 2017 和 [.NET Core CLI](../../core/tools/index.md) 都包含建立 .NET Standard 程式庫的工具支援。

如果您安裝具有 **.Net Core 跨平臺開發** 工作負載的 Visual Studio，您可以使用專案範本來建立 .NET Standard 2.0 程式庫專案，如下圖所示：

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C#](#tab/csharp)

![新增 .NET Standard 程式庫專案](./media/std-project-cs.png)

如果您使用的是 .NET Core CLI，下列 [dotnet new](../../core/tools/dotnet-new.md) 命令會建立以 .NET Standard 2.0 為目標的類別庫專案：

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

![新增 .NET Standard 程式庫專案](./media/std-project-vb.png)

如果您使用的是 .NET Core CLI，下列 [dotnet new](../../core/tools/dotnet-new.md) 命令會建立以 .NET Standard 2.0 為目標的類別庫專案：

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>請參閱

- [.NET Standard](../net-standard.md)
- [.NET Standard 簡介](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
- [下載 .NET SDK](https://dotnet.microsoft.com/download)

---
title: .NET Standard 的新功能
description: 本文摘要說明 .NET Standard 的每個新版本中的新功能和增強功能。
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45e67fe1436863da4050342bb224d67894111cc4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712483"
---
# <a name="whats-new-in-the-net-standard"></a>.NET Standard 的新功能

.NET Standard 是定義 API 的版本集正式規格，必須能在遵守該版本標準的 .NET 實作中取得。 .NET Standard 是以程式庫開發人員為目標。 以 .NET Standard 版本為目標的程式庫可以用於任何支援該標準的版本之 .NET Framework、.NET Core 或 Xamarin 實作。

.NET Standard 的最新版本為 2.0。 它包含在 .NET Core 2.0 SDK 中，也包含在已安裝 .NET Core 工作負載的 Visual Studio 2017 15.3 版中。

## <a name="supported-net-implementations"></a>支援的 .NET 實作

.NET Standard 2.0 支援下列.NET 實作：

- .NET Core 2.0 或更新版本
- .NET Framework 4.6.1 或更新版本
- Mono 5.4 或更新版本
- Xamarin.iOS 10.14 或更新版本
- Xamarin.Mac 3.8 或更新版本
- Xamarin.Android 8.0 或更新版本
- 通用 Windows 平台 10.0.16299 或更新版本

## <a name="whats-new-in-the-net-standard-20"></a>.NET Standard 2.0 的新功能

.NET Standard 2.0 包含下列新功能：

### <a name="a-vastly-expanded-set-of-apis"></a>一組大幅擴充的 API

透過 1.6 版，.NET Standard 包含相較小的 API 子集。 其中排除那些經常用於 .NET Framework 或 Xamarin 的許多 API。 這讓開發變得複雜，因為當開發人員開發以多個 .NET 實作為目標的應用程式和程式庫時，他們必須尋找熟悉的 API 之合適替代方案。 .NET Standard 2.0 藉由新增比在 .NET Standard 1.6 (前一版本) 中還多 20,000 多個 API 來解決此限制。 如需新增到 .NET Standard 2.0 的 API 清單，請參閱 [.NET Standard 2.0 與 1.6 的差異](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md) \(英文\)。

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

絕大多數的程式庫都是以 .NET Framework 為目標而不是 .NET Standard。 不過，那些程式庫中的大部分呼叫都是呼叫 .NET Standard 2.0 中包含的 API。 從 .NET Standard 2.0 開始，您可以使用[相容性填充碼](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification) \(英文\) 從 .NET Standard 程式庫存取 .NET Framework。 此相容性層級對開發人員是透明的，您不需要執行任何動作就能利用.NET Framework 程式庫。

唯一的要求是由 .NET Framework Class Library 呼叫的 API 必須包含在 .NET Standard 2.0 中。

### <a name="support-for-visual-basic"></a>Visual Basic 的支援

您現在可以在 Visual Basic 中開發 .NET Standard 程式庫。 對於使用已安裝 .NET Core 工作負載的 Visual Studio 2017 15.3 版或更新版本的 Visual Basic 開發人員，Visual Studio 現在包含 .NET Standard Class Library 範本。 對於使用其他開發工具和環境的 Visual Basic 開發人員，您可以使用 [dotnet new](../../core/tools/dotnet-new.md) 命令來建立 .NET Standard 程式庫專案。 如需詳細資訊，請參閱 [.NET Standard 程式庫的工具支援](#tooling-support-for-net-standard-libraries)。

### <a name="tooling-support-for-net-standard-libraries"></a>.NET Standard 程式庫的工具支援

隨 .NET Core 2.0 和 .NET Standard 2.0 的發行，Visual Studio 2017 和 [.NET Core 命令列介面 (CLI)](../../core/tools/index.md) 也都包含建立 .NET Standard 程式庫的工具支援。

如果您安裝包含 **.NET Core 跨平台開發**工作負載的 Visual Studio，就可以使用專案範本來建立 .NET Standard 2.0 程式庫專案，如下圖所示：

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

![新增 .NET Standard 程式庫專案](./media/std-project-cs.png)

如果您是使用 .NET Core CLI，下列 [dotnet new](../../core/tools/dotnet-new.md) 命令會建立以 .NET Standard 2.0 為目標的類別庫專案：

```
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

![新增 .NET Standard 程式庫專案](./media/std-project-vb.png)

如果您是使用 .NET Core CLI，下列 [dotnet new](../../core/tools/dotnet-new.md) 命令會建立以 .NET Standard 2.0 為目標的類別庫專案：

```
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>另請參閱

- [.NET Standard](../net-standard.md)
- [.NET Standard 簡介](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)

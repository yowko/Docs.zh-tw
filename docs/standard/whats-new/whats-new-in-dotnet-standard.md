---
title: "在.NET 標準最新消息"
ms.custom: updateeachrelease
ms.date: 11/08/2017
ms.prod: .net
ms.topic: article
ms.technology: dotnet-standard
ms.##devlang: dotnet
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e938c009b79af3b2f36094bbb74f4d38baeeac0b
ms.sourcegitcommit: 281070dee88db86ec3bb4634d5f558d1a4e159dd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2017
---
# <a name="whats-new-in-the-net-standard"></a>在.NET 標準最新消息

.NET 標準會定義一組版本必須符合標準的該版本的.NET 實作應用程式開發介面的型式規格。 .NET Standard 是以程式庫開發人員為目標。 以.NET 標準的版本為目標的程式庫可以用於任何支援的標準版的.NET Framework 中，.NET Core 或 Xamarin 實作。

.NET 標準的最新版本為 2.0。 它是為了搭配.NET Core 2.0 SDK，以及 Visual Studio 2017 版本 15.3 與安裝的.NET Core 工作負載。

## <a name="supported-net-implementations"></a>支援的.NET 實作

標準.NET 2.0 支援下列.NET 實作：

- .NET core 2.0
- .NET Framework 4.6.1
- 單聲道 5.4
- Xamarin.iOS 10.14
- Xamarin.Mac 3.8
- Xamarin.Android 8.0
- 通用 Windows 平台 10.0.16299

## <a name="whats-new-in-the-net-standard-20"></a>標準.NET 2.0 中最新消息
 
標準.NET 2.0 包含下列新功能：

**一組大幅擴充的應用程式開發介面**

1.6 版中，透過.NET 標準包含應用程式開發介面相當小的子集。 當中排除的許多常用的.NET Framework 或 Xamarin 中使用應用程式開發介面。 這讓事情更加開發，因為它需要開發人員在他們所開發的應用程式和程式庫的目標多個.NET 實作時，會尋找合適的熟悉的應用程式開發介面的取代。 標準.NET 2.0 藉由新增超過 20,000 多個應用程式開發介面比可用的.NET 標準 1.6，舊版的標準解決這項限制。 如需已新增至.NET 標準 2.0 Api，請參閱[.NET 標準 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md)。 

有些附加的<xref:System>.NET Standard 2.0 中的命名空間包含：

- 支援<xref:System.AppDomain>類別。
- 更佳的使用中的其他成員的陣列支援<xref:System.Array>類別。
- 更佳的使用中的其他成員的屬性支援<xref:System.Attribute>類別。
- 支援和其他格式選項更好行事曆<xref:System.DateTime>值。
- 其他<xref:System.Decimal>捨入的功能。
- 中的其他功能<xref:System.Environment>類別。
- 增強透過記憶體回收行程控制<xref:System.GC>類別。
- 增強的支援字串比較、 列舉型別，以及在正規化<xref:System.String>類別。
- 支援日光節約調整和轉換次數<xref:System.TimeZoneInfo.AdjustmentRule>和<xref:System.TimeZoneInfo.TransitionTime>類別。
- 中的功能中大幅增強<xref:System.Type>類別。
- 加強支援還原序列化的例外狀況物件所加入的例外狀況建構函式<xref:System.Runtime.Serialization.SerializationInfo>和<xref:System.Runtime.Serialization.StreamingContext>參數。

**.NET Framework 程式庫支援**

非常龐大的大部分程式庫的目標.NET Framework，而不是標準.NET。 不過，大部分的這些文件庫中的呼叫會隨附的.NET 標準 2.0 api。 從.NET 標準 2.0 開始，您可以存取.NET Framework 程式庫從.NET 標準程式庫使用[相容性填充碼](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification)。 此相容性層級而言是透明開發人員;您沒有執行任何動作來充分利用.NET Framework 程式庫。

一個需求是.NET Framework 類別庫所呼叫之 Api 都必須包含在標準.NET 2.0。

**適用於 Visual Basic 的支援**

您現在可以開發在 Visual Basic 中的.NET 標準程式庫。 適用於 Visual Basic 開發人員使用 Visual Studio 2017 版本 15.3 或更新版本安裝的.NET Core 工作負載，Visual Studio 現在包含.NET 標準的類別庫範本。 使用其他開發工具和環境的 Visual Basic 開發人員，您可以使用[dotnet 新](../../core/tools/dotnet-new.md)命令建立的.NET 標準程式庫專案。 如需詳細資訊，請參閱[工具支援的.NET 標準程式庫](#tooling)。

<a name="tooling" />**工具支援的.NET 標準程式庫**

版的.NET Core 2.0 和.NET Standard 2.0 中，這兩個 Visual Studio 2017 和[.NET Core 命令列介面 (CLI)](../../core/tools/index.md)包含工具支援建立.NET 標準程式庫。 

如果您安裝 Visual Studio 中以**.NET Core 跨平台開發**工作負載，您可以建立的.NET 標準 2.0 程式庫專案所使用的專案範本，如下圖所示。 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![加入新.NET 標準程式庫專案](./media/std-project-cs.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
<a name="add-new-net-standard-library-projectmediastd-project-vbpng"></a>![加入新.NET 標準程式庫專案](./media/std-project-vb.png)
---

如果您使用.NET 核心 CLI 下列[dotnet 新](../../core/tools/dotnet-new.md)命令會建立以.NET 標準 2.0 為目標的類別庫專案。

```csharp
dotnet new classlib
```
```vb
dotnet new classlib -lang vb
```
  
## <a name="see-also"></a>另請參閱
[.NET 標準](../net-standard.md)
[導入.NET 標準](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)

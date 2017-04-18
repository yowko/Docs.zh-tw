---
title: ".NET 架構元件"
description: "說明主要的 .NET 架構元件，例如，.NET 標準程式庫、.NET 執行階段和工具。"
keywords: ".NET, .NET 標準程式庫, .NET 標準, .NET Core, .NET Framework, Xamarin, MSBuild, C#, F#, VB, 編譯器"
author: cartermp
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 2e38e9d9-8284-46ee-a15f-199adc4f26f4
translationtype: Human Translation
ms.sourcegitcommit: 7741df222250f3746abb1e3c359bd9e89e6a732c
ms.openlocfilehash: e93764ff4d3391110c79f73a34512bd073ce0499
ms.lasthandoff: 04/18/2017

---

# <a name="net-architectural-components"></a>.NET 架構元件

.NET 是由數個主要元件所組成。  它具有名為 .Standard 程式庫的標準程式庫，這是可在任何地方執行的大型 API 集合。  此標準程式庫是由三個 .NET 執行階段所實作 - .NET Framework、.NET Core，以及適用於 Xamarin 的 Mono。  .NET 語言也會在任何 .NET 執行階段執行。  此外，每個平台上均會提供工具，可讓您用以建置專案。  無論您選擇的是哪個執行階段，這些工具都一樣。

以下是先前提及的每個 .NET 元件的圖形化概觀，以及它們的相符方式。

![將所有 .NET 架構元件放在一起](media/components.png)

以下是針對上述每個主要元件的簡短說明。  

## <a name="net-standard-library"></a>.NET 標準程式庫

.NET 標準程式庫是一組由 .NET 執行階段所實作的 API。

更正式的說法是，它是一個 .NET API 的規格，其構成了一組您據以編譯程式碼的制式協定。  這些協定必須具有適用於每個 .NET 執行階段的基礎實作。  這會跨不同的 .NET 執行階段啟用可攜性，如此一來，您的程式碼便能有效地「在任何地方執行」。

.NET 標準程式庫也是一個建置目標 (即為 .NET 標準)。  您目前可將目標設定為 .NET 標準 1.0-1.6。  如果您的程式碼目標為某一個 .NET 標準版本，就保證其一定可在實作該版本的任何 .NET 執行階段上執行。

若要深入了解 .NET 標準程式庫以及如何將目標設為 .NET 標準，請參閱 [.NET 標準程式庫](library.md)。

## <a name="net-runtimes"></a>.NET 執行階段

Microsoft 會主動開發和維護的主要 .NET 執行階段有 3 個︰.NET Core、.NET Framework，以及適用於 Xamarin 的 Mono。

### <a name="net-core"></a>.NET Core

.NET Core 是已針對伺服器工作負載最佳化的跨平台執行階段。  它會實作 .NET 標準程式庫，這表示任何目標為 .NET 標準的程式碼都可以在 .NET Core 上執行。  它是由 ASP.NET Core 和通用 Windows 平台 (UWP) 所使用的執行階段。  它是新式且高效率的，而其設計目的是為了處理大規模的伺服器與雲端工作負載。

若要深入了解 .NET Core，請參閱 [.NET Core 指南](../core/index.md)。

### <a name="net-framework"></a>.NET Framework

.NET Framework 是自 2002年以來已存在的歷史性 .NET 執行階段。  它就是現有 .NET 開發人員一律會使用的同一個 .NET Framework。  它會實作 .NET 標準程式庫，這表示任何目標為 .NET 標準的程式碼都可以在 .NET Framework 上執行。  它包含其他 Windows 特定的 API，例如，使用 Windows Form 和 WPF 進行適用於 Windows 桌面開發的 API。  .NET Framework 最適合用來建置 Windows 傳統型應用程式。

若要深入了解 .NET Framework，請參閱 [.NET Framework 指南](../framework/index.md)。

### <a name="mono-for-xamarin"></a>適用於 Xamarin 的 Mono

Mono 是 Xamarin 應用程式所使用的執行階段。  它會實作 .NET 標準程式庫，這表示任何目標為 .NET 標準的程式碼都可以在 Xamarin 應用程式上執行。  它包含適用於 iOS、Android、Xamarin.Forms 和 Xamarin.Mac 的其他 API。  它最適合用來在 iOS 和 Android 上建置行動應用程式。

若要深入了解 Mono，請參閱 [Mono 文件](http://www.mono-project.com/docs/)。

## <a name="net-tooling-and-common-infrastructure"></a>.NET 工具和通用基礎結構

適用於 .NET 的工具在每個 .NET 實作中也很常見。  這些包括但不限於：

* .NET 語言及其編譯器
* 執行階段元件，例如 JIT 和記憶體回收行程
* .NET 專案系統 (有時稱為 "csproj"、"vbproj" 或 "fsproj")
* MSBuild，用來建置專案的建置引擎
* NuGet，適用於.NET 的 Microsoft 套件管理員
* .NET CLI，用來建置 .NET 專案的跨平台命令列介面
* 開放原始碼建置協調流程工具，例如 CAKE 和 FAKE

此處的主要重點應該是有大量的工具和基礎結構，其對於您選擇來建置應用程式的任何 .NET「類別」而言是很常見的。

## <a name="next-steps"></a>後續步驟

若要深入了解，請瀏覽下列各項：

* [.NET 標準程式庫](library.md)
* [.NET Core 指南](../core/index.md)
* [.NET Framework 指南](../framework/index.md)
* [C# 指南](../csharp/index.md)
* [F# 指南](../fsharp/index.md)
* [VB.NET 指南](../visual-basic/index.md)


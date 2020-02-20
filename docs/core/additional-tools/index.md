---
title: 其他工具
description: 支援及延伸 .NET Core 功能之其他工具的簡介。
author: mlacouture
ms.date: 02/13/2020
ms.custom: mvc
ms.openlocfilehash: c0224a1cc6cbb9ae6fa88e5f869c47a1e84289e0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451521"
---
# <a name="net-core-additional-tools-overview"></a>.NET Core 其他工具概觀

本節會編譯除了 .NET Core CLI 以外，支援和擴充 .NET Core 功能的工具清單。

## <a name="net-core-uninstall-tool"></a>.NET Core 解除安裝工具

[.Net Core 卸載工具](https://github.com/dotnet/cli-lab/releases)（`dotnet-core-uninstall`）可讓您在系統上清除 .Net core Sdk 和執行時間，只保留指定的版本。 有一組選項可用來指定要卸載的版本。

## <a name="net-core-diagnostic-tools"></a>.NET Core 診斷工具

[dotnet-計數器](../diagnostics/dotnet-counters.md)是效能監視工具，可進行第一層健全狀況監視和效能調查。

[dotnet-](../diagnostics/dotnet-dump.md)傾印提供一種方法，可在不使用原生偵錯工具的情況下收集和分析 Windows 和 Linux 核心傾印

[dotnet-trace](../diagnostics/dotnet-trace.md)會從您的應用程式收集分析資料，當您需要找出造成應用程式執行速度緩慢的情況時，會有説明。

## <a name="wcf-web-service-reference-tool"></a>WCF Web 服務參考工具

WCF （Windows Communication Foundation） [Web 服務參考工具](wcf-web-service-reference-guide.md)是 Visual Studio 的連線服務提供者，它會在[Visual Studio 2017 15.5 版](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools)中進行首次推出。 此工具會從目前方案、網路位置或 WSDL 檔案中的 web 服務，抓取中繼資料。 它會產生與 .NET Core 相容的原始程式檔，並使用可供您用來存取 web 服務作業的方法來定義 WCF proxy 類別。

## <a name="wcf-dotnet-svcutil-tool"></a>WCF dotnet-svcutil 工具

WCF [dotnet-svcutil 工具](dotnet-svcutil-guide.md)是一種 .net 工具，可從網路位置或 WSDL 檔案中的 web 服務抓取中繼資料。 它會產生與 .NET Core 相容的原始程式檔，並使用可供您用來存取 web 服務作業的方法來定義 WCF proxy 類別。

**Dotnet-svcutil**工具是[**WCF Web 服務參考**](wcf-web-service-reference-guide.md)Visual Studio 連線服務提供者的替代方案，第一次隨附于 Visual Studio 2017 15.5 版。 以 .NET 工具形式提供的**dotnet svcutil**工具，可在 Linux、MacOS 和 Windows 上取得。

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a>WCF dotnet-svcutil： xmlserializer 工具

在 .NET Framework 上，您可以使用 svcutil 預先產生序列化組件。 WCF [dotnet-svcutil 工具](dotnet-svcutil.xmlserializer-guide.md)在 .net Core 上提供類似的功能。 它會為用戶端應用程式中由 WCF 服務合約使用且可由 <xref:System.Xml.Serialization.XmlSerializer> 序列化的類型預先產生 C# 序列化程式碼。 這可改進當序列化或還原序列化那些類型的物件時的 XML 序列化啟動效能。

## <a name="xml-serializer-generator"></a>XML 序列化程式產生器

[Microsoft.XmlSerializer.Generator NuGet 套件](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md)類似於 [Xml 序列化程式產生器 (sgen.exe)](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)，是適用於 NET Core 與 .NET Standard 程式庫的解決方案。 此套件能夠為組件中包含的類型建立 XML 序列化組件，可在將這些類型的物件序列化或還原序列化時，使用 <xref:System.Xml.Serialization.XmlSerializer> 來提升 XML 序列化的啟動效能。

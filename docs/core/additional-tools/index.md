---
title: 其他工具
description: 支援及延伸 .NET Core 功能之其他工具的簡介。
author: mlacouture
ms.date: 02/13/2020
ms.custom: mvc
ms.openlocfilehash: c0224a1cc6cbb9ae6fa88e5f869c47a1e84289e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77451521"
---
# <a name="net-core-additional-tools-overview"></a>.NET Core 其他工具概觀

本節除了 .NET Core CLI 外，還編譯支援和擴展 .NET Core 功能的工具清單。

## <a name="net-core-uninstall-tool"></a>.NET Core 解除安裝工具

[.NET 核心卸載工具](https://github.com/dotnet/cli-lab/releases)（`dotnet-core-uninstall`） 允許您在系統上清理 .NET 核心 SDK 和運行時，以便僅保留指定的版本。 選項組合可用於指定卸載的版本。

## <a name="net-core-diagnostic-tools"></a>.NET 核心診斷工具

[點網計數器](../diagnostics/dotnet-counters.md)是一級運行狀況監控和性能調查的性能監控工具。

[dotnet 轉儲](../diagnostics/dotnet-dump.md)提供了一種無需本機調試器收集和分析 Windows 和 Linux 核心轉儲的方法。

[dotnet-trace](../diagnostics/dotnet-trace.md)從你的應用收集分析資料，在您需要找出導致應用運行速度慢的方案中，這些資料會有所説明。

## <a name="wcf-web-service-reference-tool"></a>WCF Web 服務參考工具

WCF（Windows 通信基金會） [Web 服務參考工具](wcf-web-service-reference-guide.md)是一個 Visual Studio 互聯服務提供者，在[Visual Studio 2017 版 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools)中首次亮相。 此工具從當前解決方案中的 Web 服務、網路位置或 WSDL 檔案中檢索中繼資料。 它生成與 .NET Core 相容的原始檔案，使用可用於訪問 Web 服務操作的方法定義 WCF 代理類。

## <a name="wcf-dotnet-svcutil-tool"></a>WCF dotnet-svcutil 工具

WCF[點網-svcutil 工具](dotnet-svcutil-guide.md)是一個 .NET 工具，用於從網路位置的 Web 服務或從 WSDL 檔案檢索中繼資料。 它生成與 .NET Core 相容的原始檔案，使用可用於訪問 Web 服務操作的方法定義 WCF 代理類。

**dotnet-svcutil**工具是[**WCF Web 服務參考**](wcf-web-service-reference-guide.md)視覺化工作室連接服務提供者的替代方案，該服務提供者首次隨 Visual Studio 2017 版本 15.5 一起提供。 作為 .NET 工具的**dotnet-svcutil**工具在 Linux、macOS 和 Windows 上可用。

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a>WCF dotnet-svcutil.xmlserializer 工具

在 .NET Framework 上，您可以使用 svcutil 預先產生序列化組件。 WCF[點網-svcutil.xml 序列化器工具](dotnet-svcutil.xmlserializer-guide.md)在 .NET Core 上提供類似的功能。 它會為用戶端應用程式中由 WCF 服務合約使用且可由 <xref:System.Xml.Serialization.XmlSerializer> 序列化的類型預先產生 C# 序列化程式碼。 這可改進當序列化或還原序列化那些類型的物件時的 XML 序列化啟動效能。

## <a name="xml-serializer-generator"></a>XML 序列化程式產生器

[Microsoft.XmlSerializer.Generator NuGet 套件](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)類似於 [Xml 序列化程式產生器 (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md)，是適用於 NET Core 與 .NET Standard 程式庫的解決方案。 此套件能夠為組件中包含的類型建立 XML 序列化組件，可在將這些類型的物件序列化或還原序列化時，使用 <xref:System.Xml.Serialization.XmlSerializer> 來提升 XML 序列化的啟動效能。

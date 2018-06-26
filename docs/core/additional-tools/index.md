---
title: .NET Core 其他工具
description: 支援和延伸 .NET Core 功能之其他工具的簡介。
author: mlacouture
ms.author: johalex
ms.date: 01/19/2018
ms.custom: mvc
ms.openlocfilehash: 5f744fd63116ac453a2a7db8eb94f12738c95f21
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315195"
---
# <a name="net-core-additional-tools"></a>.NET Core 其他工具

本節編製了一份清單，內容涵蓋支援和延伸 .NET Core 功能的工具，以及 [.NET Core 命令列介面 (CLI)](..\tools\index.md) 工具。

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[WCF Web Service Reference 工具](wcf-web-service-reference-guide.md)

WCF (Windows Communication Foundation) Web Service Reference 是與 Visual Studio 連線的服務提供者，首次推出於 [Visual Studio 2017 15.5 版](https://visualstudio.microsoft.com/news/releasenotes/vs2017-relnotes#WCFTools)。 此工具可從目前方案中的 Web 服務、網路位置或 WSDL 檔案擷取中繼資料，且能產生與 .NET Core 相容的原始程式檔 ，其中定義的 WCF Proxy 類別與方法可讓您用於存取 Web 服務作業。

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[WCF dotnet-svcutil 工具](dotnet-svcutil-guide.md)

WCF (Windows Communication Foundation) dotnet-svcutil 工具是一種 .NET Core CLI 工具，可從 Web 服務、網路位置或 WSDL 檔案擷取中繼資料，且能產生與 .NET Core 相容的原始程式檔 ，其中定義的 WCF Proxy 類別與方法可讓您用於存取 Web 服務作業。 **dotnet-svcutil** 工具是 [**WCF Web Service Reference**](/dotnet/core/additional-tools/wcf-web-service-reference-guide) 的替代選項，後者是與 Visual Studio 連線的服務提供者，首次推出於 Visual Studio 2017 15.5 版。 **dotnet-svcutil** 工具可當作 .NET Core CLI 工具，在 Linux、macOS 和 Windows 上跨平台使用。

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML 序列化程式產生器](xml-serializer-generator.md)

[Microsoft.XmlSerializer.Generator NuGet 套件](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)類似於 [Xml 序列化程式產生器 (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md)，是適用於 NET Core 與 .NET Standard 程式庫的解決方案。 此套件能夠為組件中包含的類型建立 XML 序列化組件，可在將這些類型的物件序列化或還原序列化時，使用 <xref:System.Xml.Serialization.XmlSerializer> 來提升 XML 序列化的啟動效能。
---
title: .NET Core 其他 CLI 工具
description: 支援及延伸 .NET Core 功能之其他工具的簡介。
author: mlacouture
ms.date: 11/27/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: 5f42cddc31204bba2aafaee0b909bbf92d232fde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644288"
---
# <a name="net-core-additional-tools-overview"></a>.NET Core 其他工具概觀

本節編製了一份清單，內容涵蓋支援和延伸 .NET Core 功能的工具，以及 [.NET Core 命令列介面 (CLI)](../tools/index.md) 工具。

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[WCF Web Service Reference 工具](wcf-web-service-reference-guide.md)

WCF (Windows Communication Foundation) Web Service Reference 是與 Visual Studio 連線的服務提供者，首次推出於 [Visual Studio 2017 15.5 版](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools)。 此工具可從目前方案中的 Web 服務、網路位置或 WSDL 檔案擷取中繼資料，且能產生與 .NET Core 相容的原始程式檔 ，其中定義的 WCF Proxy 類別與方法可讓您用於存取 Web 服務作業。

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[WCF dotnet-svcutil 工具](dotnet-svcutil-guide.md)

WCF (Windows Communication Foundation) dotnet-svcutil 工具是一種 .NET Core CLI 工具，可從 Web 服務、網路位置或 WSDL 檔案擷取中繼資料，且能產生與 .NET Core 相容的原始程式檔 ，其中定義的 WCF Proxy 類別與方法可讓您用於存取 Web 服務作業。
**dotnet-svcutil** 工具是 [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) 的替代選項，後者是與 Visual Studio 連線的服務提供者，首次推出於 Visual Studio 2017 15.5 版。 **dotnet-svcutil** 工具可當作 .NET Core CLI 工具，在 Linux、macOS 和 Windows 上跨平台使用。

## <a name="wcf-dotnet-svcutilxmlserializer-tooldotnet-svcutilxmlserializer-guidemd"></a>[WCF dotnet-svcutil.xmlserializer 工具](dotnet-svcutil.xmlserializer-guide.md)

在 .NET Framework 上，您可以使用 svcutil 預先產生序列化組件。 dotnet-svcutil.xmlserializer NuGet 套件在 .NET Core 上提供類似的功能。 它會為用戶端應用程式中由 WCF 服務合約使用且可由 <xref:System.Xml.Serialization.XmlSerializer> 序列化的類型預先產生 C# 序列化程式碼。 這可改進當序列化或還原序列化那些類型的物件時的 XML 序列化啟動效能。

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML 序列化程式產生器](xml-serializer-generator.md)

[Microsoft.XmlSerializer.Generator NuGet 套件](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)類似於 [Xml 序列化程式產生器 (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md)，是適用於 NET Core 與 .NET Standard 程式庫的解決方案。 此套件能夠為組件中包含的類型建立 XML 序列化組件，可在將這些類型的物件序列化或還原序列化時，使用 <xref:System.Xml.Serialization.XmlSerializer> 來提升 XML 序列化的啟動效能。
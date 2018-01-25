---
title: ".NET Core 其他工具"
description: "支援和延伸 .NET Core 功能之其他工具的簡介。"
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2018
ms.topic: article
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: 21fcc1190ee4586a8d7eb6fb8d63a7c312e63825
ms.sourcegitcommit: c1904b0437605a90e5aa65b4abd7e048000e349d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2018
---
# <a name="net-core-additional-tools"></a>.NET Core 其他工具

本節編製了一份清單，內容涵蓋支援和延伸 .NET Core 功能的工具，以及 [.NET Core 命令列介面 (CLI)](..\tools\index.md) 工具。

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[WCF Web Service Reference 工具](wcf-web-service-reference-guide.md)

WCF Web Service Reference 是與 Visual Studio 連線的服務提供者，首次推出於 [Visual Studio 2017 15.5 版](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools)。 此工具可從目前解決方案中的 Web 服務、網路位置或 WSDL 檔案擷取中繼資料，且能產生與 .NET Core 相容的來源檔案，其中包含的 Windows Communication Foundation (WCF) 用戶端 Proxy 程式碼可讓您用於存取 Web 服務。

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML 序列化程式產生器](xml-serializer-generator.md)

[Microsoft.XmlSerializer.Generator NuGet 套件](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)類似於 [Xml 序列化程式產生器 (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md)，是適用於 NET Core 與 .NET Standard 程式庫的解決方案。 此套件能夠為組件中包含的類型建立 XML 序列化組件，可在將這些類型的物件序列化或還原序列化時，使用 <xref:System.Xml.Serialization.XmlSerializer> 來提升 XML 序列化的啟動效能。
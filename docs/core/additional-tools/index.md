---
title: 其他工具
description: 概述您可安裝的其他工具，以支援及擴充 .NET 功能。
author: mlacouture
ms.date: 02/13/2020
ms.custom: mvc
ms.openlocfilehash: 243f2da1c6f7809ac710c9700ea4cbde6f289295
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216391"
---
# <a name="net-additional-tools-overview"></a>.NET 其他工具總覽

除了 .NET CLI 之外，本節還會編譯支援和擴充 .NET 功能的工具清單。

## <a name="net-uninstall-tool"></a>.NET 卸載工具

[.Net 卸載工具](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) 可讓您清除系統上的 .Net sdk 和執行時間，使其只保留指定的版本。 選項的集合可以用來指定要卸載的版本。

## <a name="net-diagnostic-tools"></a>.NET 診斷工具

[dotnet-計數器](../diagnostics/dotnet-counters.md) 是效能監視工具，適用于第一層健康情況監視和效能調查。

[dotnet-](../diagnostics/dotnet-dump.md) 傾印提供在不使用原生偵錯工具的情況下，收集和分析 Windows 和 Linux 核心傾印的方法。

[dotnet-gcdump](../diagnostics/dotnet-gcdump.md) 可讓您收集 GC (垃圾收集行程，) 即時 .net 進程的傾印。

[dotnet](../diagnostics/dotnet-trace.md) 會從您的應用程式收集分析資料，在需要找出導致應用程式執行速度變慢的案例中有所説明。

## <a name="net-install-tool-for-extension-authors"></a>延伸模組作者的 .NET 安裝工具

[延伸模組作者的 .Net 安裝工具](https://github.com/dotnet/vscode-dotnet-runtime)是 Visual Studio Code 的延伸模組，可讓您專門針對 VS Code 延伸模組作者取得 .net 執行時間。 這項工具的目的是要用於以 .NET 撰寫的延伸模組，並要求使用 .NET 來啟動延伸模組 (例如，語言伺服器) 。 延伸模組不能直接供使用者用來安裝 .NET 進行開發。

## <a name="wcf-web-service-reference-tool"></a>WCF Web Service Reference 工具

WCF (Windows Communication Foundation) [Web 服務參考工具](wcf-web-service-reference-guide.md) 是 Visual Studio 連線的服務提供者，可在 [Visual Studio 2017 15.5 版](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools)中進行首次推出。 此工具會從目前方案中的 web 服務、網路位置或 WSDL 檔案抓取中繼資料。 它會產生與 .NET 相容的原始程式檔，使用您可以用來存取 web 服務作業的方法來定義 WCF proxy 類別。

## <a name="wcf-dotnet-svcutil-tool"></a>WCF dotnet-svcutil 工具

WCF [dotnet-svcutil 工具](dotnet-svcutil-guide.md) 是一種 .net 工具，可從網路位置或 WSDL 檔案中的 web 服務抓取中繼資料。 它會產生與 .NET 相容的原始程式檔，使用您可以用來存取 web 服務作業的方法來定義 WCF proxy 類別。

**Dotnet-svcutil** 工具是 [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio 連線服務提供者的替代方案，第一次隨附于 Visual Studio 2017 15.5 版。 **Dotnet svcutil** 工具是 .net 工具，可在 Linux、MacOS 和 Windows 上使用。

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a>WCF dotnet-svcutil.xmlserializer 工具

在 .NET Framework 上，您可以使用 svcutil 預先產生序列化組件。 WCF [dotnet-svcutil.xml序列化程式工具](dotnet-svcutil.xmlserializer-guide.md) 在 .net 5 (和 .net Core) 和更新版本上提供類似的功能。 它會為用戶端應用程式中由 WCF 服務合約使用且可由 <xref:System.Xml.Serialization.XmlSerializer> 序列化的類型預先產生 C# 序列化程式碼。 這可改進當序列化或還原序列化那些類型的物件時的 XML 序列化啟動效能。

## <a name="xml-serializer-generator"></a>XML 序列化程式產生器

如同 [Xml 序列化程式產生器 ( # A0) ](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) 適用于 .NET Framework， [Microsoft.Xml序列化程式 NuGet 套件](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) 是以 .NET 5 (和 .net Core) 和更新版本為目標之程式庫的解決方案。 此套件能夠為組件中包含的類型建立 XML 序列化組件，可在將這些類型的物件序列化或還原序列化時，使用 <xref:System.Xml.Serialization.XmlSerializer> 來提升 XML 序列化的啟動效能。

## <a name="generating-self-signed-certificates"></a>產生 Self-Signed 憑證

您可以使用 [dotnet dev](self-signed-certificates-guide.md) 憑證來建立自我簽署憑證，以用於開發和測試案例。

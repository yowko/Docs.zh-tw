---
title: .NET Core 其他工具
description: 支援和延伸 .NET Core 功能之其他工具的簡介。
author: mlacouture
ms.author: johalex
ms.date: 01/19/2018
ms.custom: mvc
ms.openlocfilehash: ba63ef6cdc092d06e267637112070e7cd5133a45
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456379"
---
# <a name="net-core-additional-tools"></a><span data-ttu-id="72229-103">.NET Core 其他工具</span><span class="sxs-lookup"><span data-stu-id="72229-103">.NET Core additional tools</span></span>

<span data-ttu-id="72229-104">本節編製了一份清單，內容涵蓋支援和延伸 .NET Core 功能的工具，以及 [.NET Core 命令列介面 (CLI)](..\tools\index.md) 工具。</span><span class="sxs-lookup"><span data-stu-id="72229-104">This section compiles a list of tools that support and extend the .NET Core functionality, in addition to the [.NET Core command-line interface (CLI)](..\tools\index.md) tools.</span></span>

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[<span data-ttu-id="72229-105">WCF Web Service Reference 工具</span><span class="sxs-lookup"><span data-stu-id="72229-105">WCF Web Service Reference tool</span></span>](wcf-web-service-reference-guide.md)

<span data-ttu-id="72229-106">WCF (Windows Communication Foundation) Web Service Reference 是與 Visual Studio 連線的服務提供者，首次推出於 [Visual Studio 2017 15.5 版](https://visualstudio.microsoft.com/news/releasenotes/vs2017-relnotes#WCFTools)。</span><span class="sxs-lookup"><span data-stu-id="72229-106">The WCF (Windows Communication Foundation) Web Service Reference is a Visual Studio connected service provider that made its debut in [Visual Studio 2017 version 15.5](https://visualstudio.microsoft.com/news/releasenotes/vs2017-relnotes#WCFTools).</span></span> <span data-ttu-id="72229-107">此工具可從目前方案中的 Web 服務、網路位置或 WSDL 檔案擷取中繼資料，且能產生與 .NET Core 相容的原始程式檔 ，其中定義的 WCF Proxy 類別與方法可讓您用於存取 Web 服務作業。</span><span class="sxs-lookup"><span data-stu-id="72229-107">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a source file compatible with .NET Core, defining a WCF proxy class with methods that you can use to access the web service operations.</span></span>

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[<span data-ttu-id="72229-108">WCF dotnet-svcutil 工具</span><span class="sxs-lookup"><span data-stu-id="72229-108">WCF dotnet-svcutil tool</span></span>](dotnet-svcutil-guide.md)

<span data-ttu-id="72229-109">WCF (Windows Communication Foundation) dotnet-svcutil 工具是一種 .NET Core CLI 工具，可從 Web 服務、網路位置或 WSDL 檔案擷取中繼資料，且能產生與 .NET Core 相容的原始程式檔 ，其中定義的 WCF Proxy 類別與方法可讓您用於存取 Web 服務作業。</span><span class="sxs-lookup"><span data-stu-id="72229-109">The WCF (Windows Communication Foundation) dotnet-svcutil tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a source file compatible with .NET Core, defining a WCF proxy class with methods that you can use to access the web service operations.</span></span> <span data-ttu-id="72229-110">**dotnet-svcutil** 工具是 [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) 的替代選項，後者是與 Visual Studio 連線的服務提供者，首次推出於 Visual Studio 2017 15.5 版。</span><span class="sxs-lookup"><span data-stu-id="72229-110">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider which first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="72229-111">**dotnet-svcutil** 工具可當作 .NET Core CLI 工具，在 Linux、macOS 和 Windows 上跨平台使用。</span><span class="sxs-lookup"><span data-stu-id="72229-111">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[<span data-ttu-id="72229-112">XML 序列化程式產生器</span><span class="sxs-lookup"><span data-stu-id="72229-112">XML Serializer Generator</span></span>](xml-serializer-generator.md)

<span data-ttu-id="72229-113">[Microsoft.XmlSerializer.Generator NuGet 套件](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)類似於 [Xml 序列化程式產生器 (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md)，是適用於 NET Core 與 .NET Standard 程式庫的解決方案。</span><span class="sxs-lookup"><span data-stu-id="72229-113">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the solution for .NET Core and .NET Standard libraries.</span></span> <span data-ttu-id="72229-114">此套件能夠為組件中包含的類型建立 XML 序列化組件，可在將這些類型的物件序列化或還原序列化時，使用 <xref:System.Xml.Serialization.XmlSerializer> 來提升 XML 序列化的啟動效能。</span><span class="sxs-lookup"><span data-stu-id="72229-114">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>
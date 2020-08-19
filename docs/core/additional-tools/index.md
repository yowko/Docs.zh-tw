---
title: 其他工具
description: 支援及延伸 .NET Core 功能之其他工具的簡介。
author: mlacouture
ms.date: 02/13/2020
ms.custom: mvc
ms.openlocfilehash: f7bfa660f7521adf4950d5bbdd59628bb88cca4d
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557928"
---
# <a name="net-core-additional-tools-overview"></a><span data-ttu-id="d1396-103">.NET Core 其他工具概觀</span><span class="sxs-lookup"><span data-stu-id="d1396-103">.NET Core additional tools overview</span></span>

<span data-ttu-id="d1396-104">本節除了 .NET Core CLI 之外，還會編譯支援和延伸 .NET Core 功能的工具清單。</span><span class="sxs-lookup"><span data-stu-id="d1396-104">This section compiles a list of tools that support and extend the .NET Core functionality, in addition to the .NET Core CLI.</span></span>

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="d1396-105">.NET Core 解除安裝工具</span><span class="sxs-lookup"><span data-stu-id="d1396-105">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="d1396-106">[.Net Core 卸載工具](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) 可讓您清除系統上的 .net Core sdk 和執行時間，使其只保留指定的版本。</span><span class="sxs-lookup"><span data-stu-id="d1396-106">The [.NET Core Uninstall Tool](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) lets you clean up .NET Core SDKs and Runtimes on a system such that only the specified versions remain.</span></span> <span data-ttu-id="d1396-107">選項的集合可以用來指定要卸載的版本。</span><span class="sxs-lookup"><span data-stu-id="d1396-107">A collection of options is available to specify which versions are uninstalled.</span></span>

## <a name="net-core-diagnostic-tools"></a><span data-ttu-id="d1396-108">.NET Core 診斷工具</span><span class="sxs-lookup"><span data-stu-id="d1396-108">.NET Core diagnostic tools</span></span>

<span data-ttu-id="d1396-109">[dotnet-計數器](../diagnostics/dotnet-counters.md) 是效能監視工具，適用于第一層健康情況監視和效能調查。</span><span class="sxs-lookup"><span data-stu-id="d1396-109">[dotnet-counters](../diagnostics/dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span>

<span data-ttu-id="d1396-110">[dotnet-](../diagnostics/dotnet-dump.md) 傾印提供在不使用原生偵錯工具的情況下，收集和分析 Windows 和 Linux 核心傾印的方法。</span><span class="sxs-lookup"><span data-stu-id="d1396-110">[dotnet-dump](../diagnostics/dotnet-dump.md) provides a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

<span data-ttu-id="d1396-111">[dotnet-gcdump](../diagnostics/dotnet-gcdump.md) 可讓您收集 GC (垃圾收集行程，) 即時 .net 進程的傾印。</span><span class="sxs-lookup"><span data-stu-id="d1396-111">[dotnet-gcdump](../diagnostics/dotnet-gcdump.md) provides a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

<span data-ttu-id="d1396-112">[dotnet](../diagnostics/dotnet-trace.md) 會從您的應用程式收集分析資料，在需要找出導致應用程式執行速度變慢的案例中有所説明。</span><span class="sxs-lookup"><span data-stu-id="d1396-112">[dotnet-trace](../diagnostics/dotnet-trace.md) collects profiling data from your app that can help in scenarios where you need to find out what causes an app to run slow.</span></span>

## <a name="wcf-web-service-reference-tool"></a><span data-ttu-id="d1396-113">WCF Web Service Reference 工具</span><span class="sxs-lookup"><span data-stu-id="d1396-113">WCF Web Service Reference tool</span></span>

<span data-ttu-id="d1396-114">WCF (Windows Communication Foundation) [Web 服務參考工具](wcf-web-service-reference-guide.md) 是 Visual Studio 連線的服務提供者，可在 [Visual Studio 2017 15.5 版](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools)中進行首次推出。</span><span class="sxs-lookup"><span data-stu-id="d1396-114">The WCF (Windows Communication Foundation) [Web Service Reference tool](wcf-web-service-reference-guide.md) is a Visual Studio connected service provider that made its debut in [Visual Studio 2017 version 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools).</span></span> <span data-ttu-id="d1396-115">此工具會從目前方案中的 web 服務、網路位置或 WSDL 檔案抓取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d1396-115">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file.</span></span> <span data-ttu-id="d1396-116">它會產生與 .NET Core 相容的來源檔案，使用您可以用來存取 web 服務作業的方法來定義 WCF proxy 類別。</span><span class="sxs-lookup"><span data-stu-id="d1396-116">It generates a source file compatible with .NET Core, defining a WCF proxy class with methods that you can use to access the web service operations.</span></span>

## <a name="wcf-dotnet-svcutil-tool"></a><span data-ttu-id="d1396-117">WCF dotnet-svcutil 工具</span><span class="sxs-lookup"><span data-stu-id="d1396-117">WCF dotnet-svcutil tool</span></span>

<span data-ttu-id="d1396-118">WCF [dotnet-svcutil 工具](dotnet-svcutil-guide.md) 是一種 .net 工具，可從網路位置或 WSDL 檔案中的 web 服務抓取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d1396-118">The WCF [dotnet-svcutil tool](dotnet-svcutil-guide.md) is a .NET tool that retrieves metadata from a web service on a network location or from a WSDL file.</span></span> <span data-ttu-id="d1396-119">它會產生與 .NET Core 相容的來源檔案，使用您可以用來存取 web 服務作業的方法來定義 WCF proxy 類別。</span><span class="sxs-lookup"><span data-stu-id="d1396-119">It generates a source file compatible with .NET Core, defining a WCF proxy class with methods that you can use to access the web service operations.</span></span>

<span data-ttu-id="d1396-120">**Dotnet-svcutil**工具是[**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio 連線服務提供者的替代方案，第一次隨附于 Visual Studio 2017 15.5 版。</span><span class="sxs-lookup"><span data-stu-id="d1396-120">The **dotnet-svcutil** tool is an alternative to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider, which first shipped with Visual Studio 2017 version 15.5.</span></span> <span data-ttu-id="d1396-121">**Dotnet svcutil**工具是 .net 工具，可在 Linux、MacOS 和 Windows 上使用。</span><span class="sxs-lookup"><span data-stu-id="d1396-121">The **dotnet-svcutil** tool, as a .NET tool, is available on Linux, macOS, and Windows.</span></span>

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a><span data-ttu-id="d1396-122">WCF dotnet-svcutil.xmlserializer 工具</span><span class="sxs-lookup"><span data-stu-id="d1396-122">WCF dotnet-svcutil.xmlserializer tool</span></span>

<span data-ttu-id="d1396-123">在 .NET Framework 上，您可以使用 svcutil 預先產生序列化組件。</span><span class="sxs-lookup"><span data-stu-id="d1396-123">On the .NET Framework, you can pre-generate a serialization assembly using the svcutil tool.</span></span> <span data-ttu-id="d1396-124">WCF [dotnet-svcutil.xml序列化程式工具](dotnet-svcutil.xmlserializer-guide.md) 可在 .net Core 上提供類似的功能。</span><span class="sxs-lookup"><span data-stu-id="d1396-124">The WCF [dotnet-svcutil.xmlserializer tool](dotnet-svcutil.xmlserializer-guide.md) provides similar functionality on .NET Core.</span></span> <span data-ttu-id="d1396-125">它會為用戶端應用程式中由 WCF 服務合約使用且可由 <xref:System.Xml.Serialization.XmlSerializer> 序列化的類型預先產生 C# 序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="d1396-125">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="d1396-126">這可改進當序列化或還原序列化那些類型的物件時的 XML 序列化啟動效能。</span><span class="sxs-lookup"><span data-stu-id="d1396-126">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="xml-serializer-generator"></a><span data-ttu-id="d1396-127">XML 序列化程式產生器</span><span class="sxs-lookup"><span data-stu-id="d1396-127">XML Serializer Generator</span></span>

<span data-ttu-id="d1396-128">[Microsoft.XmlSerializer.Generator NuGet 套件](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)類似於 [Xml 序列化程式產生器 (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md)，是適用於 NET Core 與 .NET Standard 程式庫的解決方案。</span><span class="sxs-lookup"><span data-stu-id="d1396-128">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the solution for .NET Core and .NET Standard libraries.</span></span> <span data-ttu-id="d1396-129">此套件能夠為組件中包含的類型建立 XML 序列化組件，可在將這些類型的物件序列化或還原序列化時，使用 <xref:System.Xml.Serialization.XmlSerializer> 來提升 XML 序列化的啟動效能。</span><span class="sxs-lookup"><span data-stu-id="d1396-129">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

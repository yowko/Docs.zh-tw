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
# <a name="net-core-additional-tools-overview"></a><span data-ttu-id="b3ce5-103">.NET Core 其他工具概觀</span><span class="sxs-lookup"><span data-stu-id="b3ce5-103">.NET Core additional tools overview</span></span>

<span data-ttu-id="b3ce5-104">本節會編譯除了 .NET Core CLI 以外，支援和擴充 .NET Core 功能的工具清單。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-104">This section compiles a list of tools that support and extend the .NET Core functionality, in addition to the .NET Core CLI.</span></span>

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="b3ce5-105">.NET Core 解除安裝工具</span><span class="sxs-lookup"><span data-stu-id="b3ce5-105">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="b3ce5-106">[.Net Core 卸載工具](https://github.com/dotnet/cli-lab/releases)（`dotnet-core-uninstall`）可讓您在系統上清除 .Net core Sdk 和執行時間，只保留指定的版本。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-106">The [.NET Core Uninstall Tool](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) lets you clean up .NET Core SDKs and Runtimes on a system such that only the specified versions remain.</span></span> <span data-ttu-id="b3ce5-107">有一組選項可用來指定要卸載的版本。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-107">A collection of options is available to specify which versions are uninstalled.</span></span>

## <a name="net-core-diagnostic-tools"></a><span data-ttu-id="b3ce5-108">.NET Core 診斷工具</span><span class="sxs-lookup"><span data-stu-id="b3ce5-108">.NET Core diagnostic tools</span></span>

<span data-ttu-id="b3ce5-109">[dotnet-計數器](../diagnostics/dotnet-counters.md)是效能監視工具，可進行第一層健全狀況監視和效能調查。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-109">[dotnet-counters](../diagnostics/dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span>

<span data-ttu-id="b3ce5-110">[dotnet-](../diagnostics/dotnet-dump.md)傾印提供一種方法，可在不使用原生偵錯工具的情況下收集和分析 Windows 和 Linux 核心傾印</span><span class="sxs-lookup"><span data-stu-id="b3ce5-110">[dotnet-dump](../diagnostics/dotnet-dump.md) provides a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

<span data-ttu-id="b3ce5-111">[dotnet-trace](../diagnostics/dotnet-trace.md)會從您的應用程式收集分析資料，當您需要找出造成應用程式執行速度緩慢的情況時，會有説明。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-111">[dotnet-trace](../diagnostics/dotnet-trace.md) collects profiling data from your app that can help in scenarios where you need to find out what causes an app to run slow.</span></span>

## <a name="wcf-web-service-reference-tool"></a><span data-ttu-id="b3ce5-112">WCF Web 服務參考工具</span><span class="sxs-lookup"><span data-stu-id="b3ce5-112">WCF Web Service Reference tool</span></span>

<span data-ttu-id="b3ce5-113">WCF （Windows Communication Foundation） [Web 服務參考工具](wcf-web-service-reference-guide.md)是 Visual Studio 的連線服務提供者，它會在[Visual Studio 2017 15.5 版](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools)中進行首次推出。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-113">The WCF (Windows Communication Foundation) [Web Service Reference tool](wcf-web-service-reference-guide.md) is a Visual Studio connected service provider that made its debut in [Visual Studio 2017 version 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools).</span></span> <span data-ttu-id="b3ce5-114">此工具會從目前方案、網路位置或 WSDL 檔案中的 web 服務，抓取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-114">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file.</span></span> <span data-ttu-id="b3ce5-115">它會產生與 .NET Core 相容的原始程式檔，並使用可供您用來存取 web 服務作業的方法來定義 WCF proxy 類別。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-115">It generates a source file compatible with .NET Core, defining a WCF proxy class with methods that you can use to access the web service operations.</span></span>

## <a name="wcf-dotnet-svcutil-tool"></a><span data-ttu-id="b3ce5-116">WCF dotnet-svcutil 工具</span><span class="sxs-lookup"><span data-stu-id="b3ce5-116">WCF dotnet-svcutil tool</span></span>

<span data-ttu-id="b3ce5-117">WCF [dotnet-svcutil 工具](dotnet-svcutil-guide.md)是一種 .net 工具，可從網路位置或 WSDL 檔案中的 web 服務抓取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-117">The WCF [dotnet-svcutil tool](dotnet-svcutil-guide.md) is a .NET tool that retrieves metadata from a web service on a network location or from a WSDL file.</span></span> <span data-ttu-id="b3ce5-118">它會產生與 .NET Core 相容的原始程式檔，並使用可供您用來存取 web 服務作業的方法來定義 WCF proxy 類別。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-118">It generates a source file compatible with .NET Core, defining a WCF proxy class with methods that you can use to access the web service operations.</span></span>

<span data-ttu-id="b3ce5-119">**Dotnet-svcutil**工具是[**WCF Web 服務參考**](wcf-web-service-reference-guide.md)Visual Studio 連線服務提供者的替代方案，第一次隨附于 Visual Studio 2017 15.5 版。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-119">The **dotnet-svcutil** tool is an alternative to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider, which first shipped with Visual Studio 2017 version 15.5.</span></span> <span data-ttu-id="b3ce5-120">以 .NET 工具形式提供的**dotnet svcutil**工具，可在 Linux、MacOS 和 Windows 上取得。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-120">The **dotnet-svcutil** tool, as a .NET tool, is available on Linux, macOS, and Windows.</span></span>

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a><span data-ttu-id="b3ce5-121">WCF dotnet-svcutil： xmlserializer 工具</span><span class="sxs-lookup"><span data-stu-id="b3ce5-121">WCF dotnet-svcutil.xmlserializer tool</span></span>

<span data-ttu-id="b3ce5-122">在 .NET Framework 上，您可以使用 svcutil 預先產生序列化組件。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-122">On the .NET Framework, you can pre-generate a serialization assembly using the svcutil tool.</span></span> <span data-ttu-id="b3ce5-123">WCF [dotnet-svcutil 工具](dotnet-svcutil.xmlserializer-guide.md)在 .net Core 上提供類似的功能。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-123">The WCF [dotnet-svcutil.xmlserializer tool](dotnet-svcutil.xmlserializer-guide.md) provides similar functionality on .NET Core.</span></span> <span data-ttu-id="b3ce5-124">它會為用戶端應用程式中由 WCF 服務合約使用且可由 <xref:System.Xml.Serialization.XmlSerializer> 序列化的類型預先產生 C# 序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-124">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="b3ce5-125">這可改進當序列化或還原序列化那些類型的物件時的 XML 序列化啟動效能。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-125">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="xml-serializer-generator"></a><span data-ttu-id="b3ce5-126">XML 序列化程式產生器</span><span class="sxs-lookup"><span data-stu-id="b3ce5-126">XML Serializer Generator</span></span>

<span data-ttu-id="b3ce5-127">[Microsoft.XmlSerializer.Generator NuGet 套件](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md)類似於 [Xml 序列化程式產生器 (sgen.exe)](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)，是適用於 NET Core 與 .NET Standard 程式庫的解決方案。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-127">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the solution for .NET Core and .NET Standard libraries.</span></span> <span data-ttu-id="b3ce5-128">此套件能夠為組件中包含的類型建立 XML 序列化組件，可在將這些類型的物件序列化或還原序列化時，使用 <xref:System.Xml.Serialization.XmlSerializer> 來提升 XML 序列化的啟動效能。</span><span class="sxs-lookup"><span data-stu-id="b3ce5-128">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

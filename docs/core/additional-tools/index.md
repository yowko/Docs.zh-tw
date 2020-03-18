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
# <a name="net-core-additional-tools-overview"></a><span data-ttu-id="60f09-103">.NET Core 其他工具概觀</span><span class="sxs-lookup"><span data-stu-id="60f09-103">.NET Core additional tools overview</span></span>

<span data-ttu-id="60f09-104">本節除了 .NET Core CLI 外，還編譯支援和擴展 .NET Core 功能的工具清單。</span><span class="sxs-lookup"><span data-stu-id="60f09-104">This section compiles a list of tools that support and extend the .NET Core functionality, in addition to the .NET Core CLI.</span></span>

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="60f09-105">.NET Core 解除安裝工具</span><span class="sxs-lookup"><span data-stu-id="60f09-105">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="60f09-106">[.NET 核心卸載工具](https://github.com/dotnet/cli-lab/releases)（`dotnet-core-uninstall`） 允許您在系統上清理 .NET 核心 SDK 和運行時，以便僅保留指定的版本。</span><span class="sxs-lookup"><span data-stu-id="60f09-106">The [.NET Core Uninstall Tool](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) lets you clean up .NET Core SDKs and Runtimes on a system such that only the specified versions remain.</span></span> <span data-ttu-id="60f09-107">選項組合可用於指定卸載的版本。</span><span class="sxs-lookup"><span data-stu-id="60f09-107">A collection of options is available to specify which versions are uninstalled.</span></span>

## <a name="net-core-diagnostic-tools"></a><span data-ttu-id="60f09-108">.NET 核心診斷工具</span><span class="sxs-lookup"><span data-stu-id="60f09-108">.NET Core diagnostic tools</span></span>

<span data-ttu-id="60f09-109">[點網計數器](../diagnostics/dotnet-counters.md)是一級運行狀況監控和性能調查的性能監控工具。</span><span class="sxs-lookup"><span data-stu-id="60f09-109">[dotnet-counters](../diagnostics/dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span>

<span data-ttu-id="60f09-110">[dotnet 轉儲](../diagnostics/dotnet-dump.md)提供了一種無需本機調試器收集和分析 Windows 和 Linux 核心轉儲的方法。</span><span class="sxs-lookup"><span data-stu-id="60f09-110">[dotnet-dump](../diagnostics/dotnet-dump.md) provides a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

<span data-ttu-id="60f09-111">[dotnet-trace](../diagnostics/dotnet-trace.md)從你的應用收集分析資料，在您需要找出導致應用運行速度慢的方案中，這些資料會有所説明。</span><span class="sxs-lookup"><span data-stu-id="60f09-111">[dotnet-trace](../diagnostics/dotnet-trace.md) collects profiling data from your app that can help in scenarios where you need to find out what causes an app to run slow.</span></span>

## <a name="wcf-web-service-reference-tool"></a><span data-ttu-id="60f09-112">WCF Web 服務參考工具</span><span class="sxs-lookup"><span data-stu-id="60f09-112">WCF Web Service Reference tool</span></span>

<span data-ttu-id="60f09-113">WCF（Windows 通信基金會） [Web 服務參考工具](wcf-web-service-reference-guide.md)是一個 Visual Studio 互聯服務提供者，在[Visual Studio 2017 版 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools)中首次亮相。</span><span class="sxs-lookup"><span data-stu-id="60f09-113">The WCF (Windows Communication Foundation) [Web Service Reference tool](wcf-web-service-reference-guide.md) is a Visual Studio connected service provider that made its debut in [Visual Studio 2017 version 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools).</span></span> <span data-ttu-id="60f09-114">此工具從當前解決方案中的 Web 服務、網路位置或 WSDL 檔案中檢索中繼資料。</span><span class="sxs-lookup"><span data-stu-id="60f09-114">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file.</span></span> <span data-ttu-id="60f09-115">它生成與 .NET Core 相容的原始檔案，使用可用於訪問 Web 服務操作的方法定義 WCF 代理類。</span><span class="sxs-lookup"><span data-stu-id="60f09-115">It generates a source file compatible with .NET Core, defining a WCF proxy class with methods that you can use to access the web service operations.</span></span>

## <a name="wcf-dotnet-svcutil-tool"></a><span data-ttu-id="60f09-116">WCF dotnet-svcutil 工具</span><span class="sxs-lookup"><span data-stu-id="60f09-116">WCF dotnet-svcutil tool</span></span>

<span data-ttu-id="60f09-117">WCF[點網-svcutil 工具](dotnet-svcutil-guide.md)是一個 .NET 工具，用於從網路位置的 Web 服務或從 WSDL 檔案檢索中繼資料。</span><span class="sxs-lookup"><span data-stu-id="60f09-117">The WCF [dotnet-svcutil tool](dotnet-svcutil-guide.md) is a .NET tool that retrieves metadata from a web service on a network location or from a WSDL file.</span></span> <span data-ttu-id="60f09-118">它生成與 .NET Core 相容的原始檔案，使用可用於訪問 Web 服務操作的方法定義 WCF 代理類。</span><span class="sxs-lookup"><span data-stu-id="60f09-118">It generates a source file compatible with .NET Core, defining a WCF proxy class with methods that you can use to access the web service operations.</span></span>

<span data-ttu-id="60f09-119">**dotnet-svcutil**工具是[**WCF Web 服務參考**](wcf-web-service-reference-guide.md)視覺化工作室連接服務提供者的替代方案，該服務提供者首次隨 Visual Studio 2017 版本 15.5 一起提供。</span><span class="sxs-lookup"><span data-stu-id="60f09-119">The **dotnet-svcutil** tool is an alternative to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider, which first shipped with Visual Studio 2017 version 15.5.</span></span> <span data-ttu-id="60f09-120">作為 .NET 工具的**dotnet-svcutil**工具在 Linux、macOS 和 Windows 上可用。</span><span class="sxs-lookup"><span data-stu-id="60f09-120">The **dotnet-svcutil** tool, as a .NET tool, is available on Linux, macOS, and Windows.</span></span>

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a><span data-ttu-id="60f09-121">WCF dotnet-svcutil.xmlserializer 工具</span><span class="sxs-lookup"><span data-stu-id="60f09-121">WCF dotnet-svcutil.xmlserializer tool</span></span>

<span data-ttu-id="60f09-122">在 .NET Framework 上，您可以使用 svcutil 預先產生序列化組件。</span><span class="sxs-lookup"><span data-stu-id="60f09-122">On the .NET Framework, you can pre-generate a serialization assembly using the svcutil tool.</span></span> <span data-ttu-id="60f09-123">WCF[點網-svcutil.xml 序列化器工具](dotnet-svcutil.xmlserializer-guide.md)在 .NET Core 上提供類似的功能。</span><span class="sxs-lookup"><span data-stu-id="60f09-123">The WCF [dotnet-svcutil.xmlserializer tool](dotnet-svcutil.xmlserializer-guide.md) provides similar functionality on .NET Core.</span></span> <span data-ttu-id="60f09-124">它會為用戶端應用程式中由 WCF 服務合約使用且可由 <xref:System.Xml.Serialization.XmlSerializer> 序列化的類型預先產生 C# 序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="60f09-124">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="60f09-125">這可改進當序列化或還原序列化那些類型的物件時的 XML 序列化啟動效能。</span><span class="sxs-lookup"><span data-stu-id="60f09-125">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="xml-serializer-generator"></a><span data-ttu-id="60f09-126">XML 序列化程式產生器</span><span class="sxs-lookup"><span data-stu-id="60f09-126">XML Serializer Generator</span></span>

<span data-ttu-id="60f09-127">[Microsoft.XmlSerializer.Generator NuGet 套件](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)類似於 [Xml 序列化程式產生器 (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md)，是適用於 NET Core 與 .NET Standard 程式庫的解決方案。</span><span class="sxs-lookup"><span data-stu-id="60f09-127">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the solution for .NET Core and .NET Standard libraries.</span></span> <span data-ttu-id="60f09-128">此套件能夠為組件中包含的類型建立 XML 序列化組件，可在將這些類型的物件序列化或還原序列化時，使用 <xref:System.Xml.Serialization.XmlSerializer> 來提升 XML 序列化的啟動效能。</span><span class="sxs-lookup"><span data-stu-id="60f09-128">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

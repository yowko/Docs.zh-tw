---
title: .NET Framework 的組態檔結構描述
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: ab6f12be01899f5b7e54a7ec2d9675d502d88bc3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555129"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="274a4-102">.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="274a4-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="274a4-103">組態檔是標準的 XML 檔，可以用來變更應用程式的設定和設定應用程式的原則。</span><span class="sxs-lookup"><span data-stu-id="274a4-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="274a4-104">.NET Framework 組態結構描述所包含的項目可在組態檔中用來控制應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="274a4-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="274a4-105">本節的目錄反映出啟動、執行階段、網路和其他類型組態設定的結構描述階層架構。</span><span class="sxs-lookup"><span data-stu-id="274a4-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="274a4-106">如需配置檔案類型、格式和位置的相關資訊，請參閱 [設定應用程式](../index.md)。</span><span class="sxs-lookup"><span data-stu-id="274a4-106">For information about the types, format, and location of configuration files, see [Configure apps](../index.md).</span></span> <span data-ttu-id="274a4-107">如果想要直接編輯組態檔，請熟悉 XML。</span><span class="sxs-lookup"><span data-stu-id="274a4-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="274a4-108">組態檔中的 XML 標記和屬性區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="274a4-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="274a4-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="274a4-109">In this section</span></span>

<span data-ttu-id="274a4-110">[**\<configuration>** 元素](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-110">[**\<configuration>** Element](configuration-element.md)</span></span>\
<span data-ttu-id="274a4-111">所有設定檔的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="274a4-111">The top-level element for all configuration files.</span></span>

<span data-ttu-id="274a4-112">[**\<assemblyBinding>** 元素](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-112">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md)</span></span>\
<span data-ttu-id="274a4-113">指定位於組態層級的組件繫結原則。</span><span class="sxs-lookup"><span data-stu-id="274a4-113">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="274a4-114">[**\<linkedConfiguration>** 元素](linkedconfiguration-element.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-114">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md)</span></span>\
<span data-ttu-id="274a4-115">指定要包含的組態檔。</span><span class="sxs-lookup"><span data-stu-id="274a4-115">Specifies a configuration file to include.</span></span>

<span data-ttu-id="274a4-116">[啟動設定架構](./startup/index.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-116">[Startup Settings Schema](./startup/index.md)</span></span>\
<span data-ttu-id="274a4-117">元素，指定要使用的 common language runtime 版本。</span><span class="sxs-lookup"><span data-stu-id="274a4-117">Elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="274a4-118">[執行時間設定架構](./runtime/index.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-118">[Runtime Settings Schema](./runtime/index.md)</span></span>\
<span data-ttu-id="274a4-119">設定元件系結和執行時間行為的元素。</span><span class="sxs-lookup"><span data-stu-id="274a4-119">Elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="274a4-120">[網路設定架構](./network/index.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-120">[Network Settings Schema](./network/index.md)</span></span>\
<span data-ttu-id="274a4-121">指定 .NET Framework 如何連接到網際網路的元素。</span><span class="sxs-lookup"><span data-stu-id="274a4-121">Elements that specify how the .NET Framework connects to the internet.</span></span>

<span data-ttu-id="274a4-122">[密碼編譯設定架構](./cryptography/index.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-122">[Cryptography Settings Schema](./cryptography/index.md)</span></span>\
<span data-ttu-id="274a4-123">將易記的演算法名稱對應至執行密碼編譯演算法之類別的元素。</span><span class="sxs-lookup"><span data-stu-id="274a4-123">Elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="274a4-124">[設定區段架構](configuration-sections-schema.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-124">[Configuration Sections Schema](configuration-sections-schema.md)</span></span>\
<span data-ttu-id="274a4-125">用來建立及使用自訂設定之設定區段的元素。</span><span class="sxs-lookup"><span data-stu-id="274a4-125">Elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="274a4-126">[追蹤和調試設定架構](./trace-debug/index.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-126">[Trace and Debug Settings Schema](./trace-debug/index.md)</span></span>\
<span data-ttu-id="274a4-127">指定追蹤參數和接聽程式的元素。</span><span class="sxs-lookup"><span data-stu-id="274a4-127">Elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="274a4-128">[編譯器和語言提供者設定架構](./compiler/index.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-128">[Compiler and Language Provider Settings Schema](./compiler/index.md)</span></span>\
<span data-ttu-id="274a4-129">指定可用語言提供者之編譯器設定的元素。</span><span class="sxs-lookup"><span data-stu-id="274a4-129">Elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="274a4-130">[應用程式設定架構](application-settings-schema.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-130">[Application Settings Schema](application-settings-schema.md)</span></span>\
<span data-ttu-id="274a4-131">可讓 Windows Forms 或 ASP.NET 應用程式儲存和取出應用程式範圍和使用者範圍設定的元素。</span><span class="sxs-lookup"><span data-stu-id="274a4-131">Elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="274a4-132">[應用程式設定架構](./appsettings/index.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-132">[App Settings Schema](./appsettings/index.md)</span></span>\
<span data-ttu-id="274a4-133">包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。</span><span class="sxs-lookup"><span data-stu-id="274a4-133">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="274a4-134">[Web 設定架構](./web/index.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-134">[Web Settings Schema](./web/index.md)</span></span>\
<span data-ttu-id="274a4-135">用來設定 ASP.NET 如何搭配主機應用程式（例如 IIS）運作的元素。</span><span class="sxs-lookup"><span data-stu-id="274a4-135">Elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="274a4-136">用於 *Aspnet.config* 檔案。</span><span class="sxs-lookup"><span data-stu-id="274a4-136">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="274a4-137">[Windows Forms 設定架構](winforms/index.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-137">[Windows Forms Configuration Schema](winforms/index.md)</span></span>\
<span data-ttu-id="274a4-138">[Windows Forms 應用程式設定] 區段中的所有元素，包括多監視器和高 DPI 支援等自訂。</span><span class="sxs-lookup"><span data-stu-id="274a4-138">All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high-DPI support.</span></span>

<span data-ttu-id="274a4-139">[WCF 設定架構](./wcf/index.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-139">[WCF Configuration Schema](./wcf/index.md)</span></span>\
<span data-ttu-id="274a4-140">所有可讓您設定 WCF 服務和用戶端應用程式的元素。</span><span class="sxs-lookup"><span data-stu-id="274a4-140">All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="274a4-141">[WCF 指示詞語法](./wcf-directive/index.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-141">[WCF Directive Syntax](./wcf-directive/index.md)</span></span>\
<span data-ttu-id="274a4-142">描述指示詞，此指示詞會 `@ServiceHost` 定義 .svc 編譯器使用的頁面特定屬性。</span><span class="sxs-lookup"><span data-stu-id="274a4-142">Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="274a4-143">[WIF 設定架構](windows-identity-foundation/index.md)</span><span class="sxs-lookup"><span data-stu-id="274a4-143">[WIF Configuration Schema](windows-identity-foundation/index.md)</span></span>\
<span data-ttu-id="274a4-144">Windows Identity Foundation (的所有元素都會 WIF) 設定架構。</span><span class="sxs-lookup"><span data-stu-id="274a4-144">All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="274a4-145">相關章節</span><span class="sxs-lookup"><span data-stu-id="274a4-145">Related sections</span></span>

<span data-ttu-id="274a4-146">[遠端設定架構](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="274a4-146">[Remoting Settings Schema](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span>\
<span data-ttu-id="274a4-147">說明設定實作遠端處理之用戶端和伺服器應用程式的項目。</span><span class="sxs-lookup"><span data-stu-id="274a4-147">Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="274a4-148">[ASP.NET 設定架構](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="274a4-148">[ASP.NET Settings Schema](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span>\
<span data-ttu-id="274a4-149">描述控制 ASP.NET Web 應用程式之行為的項目。</span><span class="sxs-lookup"><span data-stu-id="274a4-149">Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="274a4-150">[Web 服務設定架構](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="274a4-150">[Web Services Settings Schema](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span>\
<span data-ttu-id="274a4-151">描述控制 ASP.NET Web 服務和其用戶端之行為的項目。</span><span class="sxs-lookup"><span data-stu-id="274a4-151">Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="274a4-152">[設定 .NET Framework 應用程式](/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="274a4-152">[Configuring .NET Framework Apps](/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span></span>\
<span data-ttu-id="274a4-153">描述如何在 .NET Framework 中設定安全性、組件繫結和遠端處理。</span><span class="sxs-lookup"><span data-stu-id="274a4-153">Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>

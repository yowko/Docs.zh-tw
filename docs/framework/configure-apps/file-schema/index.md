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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b227ba343db7996d38d5a485b54629a1f4ed28bd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="ed6a8-102">.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="ed6a8-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="ed6a8-103">組態檔是標準的 XML 檔，可以用來變更應用程式的設定和設定應用程式的原則。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="ed6a8-104">.NET Framework 組態結構描述所包含的項目可在組態檔中用來控制應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="ed6a8-105">本節的目錄反映出啟動、執行階段、網路和其他類型組態設定的結構描述階層架構。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="ed6a8-106">如需組態檔之類型、格式和位置的資訊，請參閱 [設定應用程式](~/docs/framework/configure-apps/index.md)一文。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-106">For information about the types, format, and location of configuration files, see the article [Configuring Apps](~/docs/framework/configure-apps/index.md).</span></span> <span data-ttu-id="ed6a8-107">如果想要直接編輯組態檔，請熟悉 XML。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ed6a8-108">組態檔中的 XML 標記和屬性區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ed6a8-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="ed6a8-109">In this section</span></span>

<span data-ttu-id="ed6a8-110">[**\<configuration>** 項目](~/docs/framework/configure-apps/file-schema/configuration-element.md) - 描述 `<configuration>` 項目，這個項目是所有組態檔的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-110">[**\<configuration>** Element](~/docs/framework/configure-apps/file-schema/configuration-element.md) Describes the `<configuration>` element, which is the top-level element for all configuration files.</span></span>

<span data-ttu-id="ed6a8-111">[**\<assemblyBinding>** 項目](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) - 指定位於組態層級的組件繫結原則。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-111">[**\<assemblyBinding>** Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="ed6a8-112">[**\<linkedConfiguration>** 項目](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) - 指定要包含的組態檔。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-112">[**\<linkedConfiguration>** Element](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) Specifies a configuration file to include.</span></span>

<span data-ttu-id="ed6a8-113">[啟動設定結構描述](~/docs/framework/configure-apps/file-schema/startup/index.md) - 描述指定要使用的 Common Language Runtime 版本的項目。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-113">[Startup Settings Schema](~/docs/framework/configure-apps/file-schema/startup/index.md) Describes the elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="ed6a8-114">[執行階段設定結構描述](~/docs/framework/configure-apps/file-schema/runtime/index.md) - 描述設定組件繫結和執行階段行為的項目。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-114">[Runtime Settings Schema](~/docs/framework/configure-apps/file-schema/runtime/index.md) Describes the elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="ed6a8-115">[網路設定結構描述](~/docs/framework/configure-apps/file-schema/network/index.md) - 描述指定 .NET Framework 連線到網際網路之方式的項目。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-115">[Network Settings Schema](~/docs/framework/configure-apps/file-schema/network/index.md) Describes the elements that specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="ed6a8-116">[密碼編譯設定結構描述](~/docs/framework/configure-apps/file-schema/cryptography/index.md) - 描述將易記的演算法名稱對應至實作密碼編譯演算法之類別的項目。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-116">[Cryptography Settings Schema](~/docs/framework/configure-apps/file-schema/cryptography/index.md) Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="ed6a8-117">[組態區段結構描述](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) - 描述用來建立和使用自訂設定之組態區段的項目。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-117">[Configuration Sections Schema](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) Describes the elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="ed6a8-118">[追蹤和偵錯設定結構描述](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) - 描述指定追蹤參數和接聽項的項目。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-118">[Trace and Debug Settings Schema](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) Describes the elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="ed6a8-119">[編譯器和語言提供者設定結構描述](~/docs/framework/configure-apps/file-schema/compiler/index.md) - 描述在指定可用的語言提供者之編譯器組態的項目。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-119">[Compiler and Language Provider Settings Schema](~/docs/framework/configure-apps/file-schema/compiler/index.md) Describes the elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="ed6a8-120">[應用程式設定結構描述](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) - 描述可讓 Windows Forms 或 ASP.NET 應用程式儲存及擷取應用程式範圍和使用者範圍設定的項目。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-120">[Application Settings Schema](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) Describes the elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="ed6a8-121">[應用程式設定結構描述](~/docs/framework/configure-apps/file-schema/appsettings/index.md) - 包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-121">[App Settings Schema](~/docs/framework/configure-apps/file-schema/appsettings/index.md) Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="ed6a8-122">[Web 設定結構描述](~/docs/framework/configure-apps/file-schema/web/index.md) - Web 設定結構描述中的所有項目，包括用來設定 ASP.NET 如何配合主機應用程式 (例如 IIS) 運作的項目。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-122">[Web Settings Schema](~/docs/framework/configure-apps/file-schema/web/index.md) All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="ed6a8-123">用於 *Aspnet.config* 檔案。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-123">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="ed6a8-124">[Windows Forms 組態結構描述](winforms/index.md) - Windows Forms 應用程式組態區段中的所有項目，包括多重監視器和高 DPI 支援等自訂項目。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-124">[Windows Forms Configuration Schema](winforms/index.md) All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high DPI support.</span></span>

<span data-ttu-id="ed6a8-125">[WCF 組態結構描述](~/docs/framework/configure-apps/file-schema/wcf/index.md) - 可讓您設定 WCF 服務與用戶端應用程式的所有項目。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-125">[WCF Configuration Schema](~/docs/framework/configure-apps/file-schema/wcf/index.md) All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="ed6a8-126">[WCF 指示詞語法](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) - 描述定義 .svc 編譯器使用之網頁專用屬性的 `@ServiceHost` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-126">[WCF Directive Syntax](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="ed6a8-127">[WIF 組態結構描述](windows-identity-foundation/index.md) - Windows Identity Foundation (WIF) 組態結構描述的所有項目。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-127">[WIF Configuration Schema](windows-identity-foundation/index.md) All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="ed6a8-128">相關章節</span><span class="sxs-lookup"><span data-stu-id="ed6a8-128">Related sections</span></span>

<span data-ttu-id="ed6a8-129">[遠端設定結構描述](http://msdn.microsoft.com/library/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) - 描述設定實作遠端處理之用戶端和伺服器應用程式的項目。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-129">[Remoting Settings Schema](http://msdn.microsoft.com/library/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="ed6a8-130">[ASP.NET 設定結構描述](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) - 描述控制 ASP.NET Web 應用程式之行為的項目。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-130">[ASP.NET Settings Schema](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="ed6a8-131">[Web 服務設定結構描述](http://msdn.microsoft.com/library/f84d6d55-1add-4eb7-ae46-33df5833ea2e) - 描述控制 ASP.NET Web 服務和其用戶端之行為的項目。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-131">[Web Services Settings Schema](http://msdn.microsoft.com/library/f84d6d55-1add-4eb7-ae46-33df5833ea2e) Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="ed6a8-132">[設定 .NET Framework 應用程式](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) - 描述如何在 .NET Framework 中設定安全性、組件繫結和遠端處理。</span><span class="sxs-lookup"><span data-stu-id="ed6a8-132">[Configuring .NET Framework Apps](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>

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
ms.openlocfilehash: c3b5518b4b86c2e6f47825d552f49579c5ac0a6d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921033"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="14292-102">.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="14292-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="14292-103">組態檔是標準的 XML 檔，可以用來變更應用程式的設定和設定應用程式的原則。</span><span class="sxs-lookup"><span data-stu-id="14292-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="14292-104">.NET Framework 組態結構描述所包含的項目可在組態檔中用來控制應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="14292-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="14292-105">本節的目錄反映出啟動、執行階段、網路和其他類型組態設定的結構描述階層架構。</span><span class="sxs-lookup"><span data-stu-id="14292-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="14292-106">如需組態檔之類型、格式和位置的資訊，請參閱 [設定應用程式](../index.md)一文。</span><span class="sxs-lookup"><span data-stu-id="14292-106">For information about the types, format, and location of configuration files, see the article [Configuring Apps](../index.md).</span></span> <span data-ttu-id="14292-107">如果想要直接編輯組態檔，請熟悉 XML。</span><span class="sxs-lookup"><span data-stu-id="14292-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="14292-108">組態檔中的 XML 標記和屬性區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="14292-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="14292-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="14292-109">In this section</span></span>

<span data-ttu-id="14292-110">[ **\<configuration>** 項目](configuration-element.md) - 描述 `<configuration>` 項目，這個項目是所有組態檔的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="14292-110">[**\<configuration>** Element](configuration-element.md) Describes the `<configuration>` element, which is the top-level element for all configuration files.</span></span>

<span data-ttu-id="14292-111">[ **\<assemblyBinding>** 項目](assemblybinding-element-for-configuration.md) - 指定位於組態層級的組件繫結原則。</span><span class="sxs-lookup"><span data-stu-id="14292-111">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md) Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="14292-112">[ **\<linkedConfiguration>** 項目](linkedconfiguration-element.md) - 指定要包含的組態檔。</span><span class="sxs-lookup"><span data-stu-id="14292-112">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md) Specifies a configuration file to include.</span></span>

<span data-ttu-id="14292-113">[啟動設定結構描述](./startup/index.md) - 描述指定要使用的 Common Language Runtime 版本的項目。</span><span class="sxs-lookup"><span data-stu-id="14292-113">[Startup Settings Schema](./startup/index.md) Describes the elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="14292-114">[執行階段設定結構描述](./runtime/index.md) - 描述設定組件繫結和執行階段行為的項目。</span><span class="sxs-lookup"><span data-stu-id="14292-114">[Runtime Settings Schema](./runtime/index.md) Describes the elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="14292-115">[網路設定結構描述](./network/index.md) - 描述指定 .NET Framework 連線到網際網路之方式的項目。</span><span class="sxs-lookup"><span data-stu-id="14292-115">[Network Settings Schema](./network/index.md) Describes the elements that specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="14292-116">[密碼編譯設定結構描述](./cryptography/index.md) - 描述將易記的演算法名稱對應至實作密碼編譯演算法之類別的項目。</span><span class="sxs-lookup"><span data-stu-id="14292-116">[Cryptography Settings Schema](./cryptography/index.md) Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="14292-117">[組態區段結構描述](configuration-sections-schema.md) - 描述用來建立和使用自訂設定之組態區段的項目。</span><span class="sxs-lookup"><span data-stu-id="14292-117">[Configuration Sections Schema](configuration-sections-schema.md) Describes the elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="14292-118">[追蹤和偵錯設定結構描述](./trace-debug/index.md) - 描述指定追蹤參數和接聽項的項目。</span><span class="sxs-lookup"><span data-stu-id="14292-118">[Trace and Debug Settings Schema](./trace-debug/index.md) Describes the elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="14292-119">[編譯器和語言提供者設定結構描述](./compiler/index.md) - 描述在指定可用的語言提供者之編譯器組態的項目。</span><span class="sxs-lookup"><span data-stu-id="14292-119">[Compiler and Language Provider Settings Schema](./compiler/index.md) Describes the elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="14292-120">[應用程式設定結構描述](application-settings-schema.md) - 描述可讓 Windows Forms 或 ASP.NET 應用程式儲存及擷取應用程式範圍和使用者範圍設定的項目。</span><span class="sxs-lookup"><span data-stu-id="14292-120">[Application Settings Schema](application-settings-schema.md) Describes the elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="14292-121">[應用程式設定結構描述](./appsettings/index.md) - 包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。</span><span class="sxs-lookup"><span data-stu-id="14292-121">[App Settings Schema](./appsettings/index.md) Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="14292-122">[Web 設定結構描述](./web/index.md) - Web 設定結構描述中的所有項目，包括用來設定 ASP.NET 如何配合主機應用程式 (例如 IIS) 運作的項目。</span><span class="sxs-lookup"><span data-stu-id="14292-122">[Web Settings Schema](./web/index.md) All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="14292-123">用於 *Aspnet.config* 檔案。</span><span class="sxs-lookup"><span data-stu-id="14292-123">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="14292-124">[Windows Forms 組態結構描述](winforms/index.md) - Windows Forms 應用程式組態區段中的所有項目，包括多重監視器和高 DPI 支援等自訂項目。</span><span class="sxs-lookup"><span data-stu-id="14292-124">[Windows Forms Configuration Schema](winforms/index.md) All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high DPI support.</span></span>

<span data-ttu-id="14292-125">[WCF 組態結構描述](./wcf/index.md) - 可讓您設定 WCF 服務與用戶端應用程式的所有項目。</span><span class="sxs-lookup"><span data-stu-id="14292-125">[WCF Configuration Schema](./wcf/index.md) All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="14292-126">[WCF 指示詞語法](./wcf-directive/index.md) - 描述定義 .svc 編譯器使用之網頁專用屬性的 `@ServiceHost` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="14292-126">[WCF Directive Syntax](./wcf-directive/index.md) Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="14292-127">[WIF 組態結構描述](windows-identity-foundation/index.md) - Windows Identity Foundation (WIF) 組態結構描述的所有項目。</span><span class="sxs-lookup"><span data-stu-id="14292-127">[WIF Configuration Schema](windows-identity-foundation/index.md) All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="14292-128">相關章節</span><span class="sxs-lookup"><span data-stu-id="14292-128">Related sections</span></span>

<span data-ttu-id="14292-129">[遠端設定結構描述](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) - 描述設定實作遠端處理之用戶端和伺服器應用程式的項目。</span><span class="sxs-lookup"><span data-stu-id="14292-129">[Remoting Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="14292-130">[ASP.NET 設定結構描述](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) - 描述控制 ASP.NET Web 應用程式之行為的項目。</span><span class="sxs-lookup"><span data-stu-id="14292-130">[ASP.NET Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="14292-131">[Web 服務設定結構描述](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) - 描述控制 ASP.NET Web 服務和其用戶端之行為的項目。</span><span class="sxs-lookup"><span data-stu-id="14292-131">[Web Services Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="14292-132">[設定 .NET Framework 應用程式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) - 描述如何在 .NET Framework 中設定安全性、組件繫結和遠端處理。</span><span class="sxs-lookup"><span data-stu-id="14292-132">[Configuring .NET Framework Apps](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>

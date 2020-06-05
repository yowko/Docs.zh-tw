---
title: 將您的 .NET Web 應用程式或服務遷移至 Azure App Service
description: 瞭解如何將 .NET web 應用程式或服務從內部部署遷移至 Azure App Service。
ms.topic: conceptual
ms.date: 08/11/2018
ms.openlocfilehash: 8761642469b6f3d3c93d2e2e0fa7e02dbf3de6d7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447000"
---
# <a name="migrate-your-net-web-app-or-service-to-azure-app-service"></a><span data-ttu-id="5a3f9-103">將您的 .NET Web 應用程式或服務遷移至 Azure App Service</span><span class="sxs-lookup"><span data-stu-id="5a3f9-103">Migrate your .NET web app or service to Azure App Service</span></span>

<span data-ttu-id="5a3f9-104">[App Service](https://docs.microsoft.com/azure/app-service/overview)是完全受控的計算平臺服務，最適合用來裝載可擴充的網站和 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-104">[App Service](https://docs.microsoft.com/azure/app-service/overview) is a fully managed compute platform service that's optimized for hosting scalable websites and web applications.</span></span> <span data-ttu-id="5a3f9-105">本文提供如何將現有的應用程式隨即轉移至 Azure App Service、考慮的修改，以及[移至雲端](https://azure.microsoft.com/migration/web-applications/)的其他資源的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-105">This article provides information on how to lift-and-shift an existing application to Azure App Service, modifications to consider, and additional resources for [moving to the cloud](https://azure.microsoft.com/migration/web-applications/).</span></span> <span data-ttu-id="5a3f9-106">大部分 ASP.NET 網站 (Webforms、MVC) 和服務 (Web API、WCF) 都可以在沒有變更的情況下直接移至 Azure App Service。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-106">Most ASP.NET websites (Webforms, MVC) and services (Web API, WCF) can move directly to Azure App Service with no changes.</span></span> <span data-ttu-id="5a3f9-107">一些服務可能需要些微變更，而其他服務則可能需要進行一些重構。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-107">Some may need minor changes while others may need some refactoring.</span></span>

<span data-ttu-id="5a3f9-108">準備好開始了嗎？</span><span class="sxs-lookup"><span data-stu-id="5a3f9-108">Ready to get started?</span></span> <span data-ttu-id="5a3f9-109">[將 ASP.NET + SQL 應用程式發佈至 Azure App Service](https://tutorials.visualstudio.com/azure-webapp-migrate/intro)。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-109">[Publish your ASP.NET + SQL application to Azure App Service](https://tutorials.visualstudio.com/azure-webapp-migrate/intro).</span></span>

## <a name="considerations"></a><span data-ttu-id="5a3f9-110">考量</span><span class="sxs-lookup"><span data-stu-id="5a3f9-110">Considerations</span></span>

### <a name="on-premises-resources-including-sql-server"></a><span data-ttu-id="5a3f9-111">內部部署資源 (包括 SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5a3f9-111">On-premises resources (including SQL Server)</span></span>

<span data-ttu-id="5a3f9-112">因為內部部署資源可能需要遷移或變更，所以請確認內部部署資源的存取權。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-112">Verify access to on-premises resources as these may need to be migrated or changed.</span></span> <span data-ttu-id="5a3f9-113">減少內部部署資源存取權的選項如下：</span><span class="sxs-lookup"><span data-stu-id="5a3f9-113">The following are options for mitigating access to on-premises resources:</span></span>

* <span data-ttu-id="5a3f9-114">使用 [Azure 虛擬網路](https://docs.microsoft.com/azure/app-service/web-sites-integrate-with-vnet)建立 VPN，讓 App Service 與內部部署資源連線。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-114">Create a VPN connecting App Service to on-premises resources using [Azure Virtual Networks](https://docs.microsoft.com/azure/app-service/web-sites-integrate-with-vnet).</span></span>
* <span data-ttu-id="5a3f9-115">使用 [Azure 轉送](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it)安全地將內部部署服務公開至雲端，而不變更防火牆。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-115">Securely expose on-premises services to the cloud without firewall changes using [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>
* <span data-ttu-id="5a3f9-116">將例如 [SQL 資料庫](https://go.microsoft.com/fwlink/?linkid=863217) 的相依性遷移至 Azure。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-116">Migrate dependencies such as a [SQL database](https://go.microsoft.com/fwlink/?linkid=863217) to Azure.</span></span>
* <span data-ttu-id="5a3f9-117">使用雲端中的平臺即服務供應專案來減少相依性。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-117">Use platform-as-a-service offerings in the cloud to reduce dependencies.</span></span> <span data-ttu-id="5a3f9-118">例如，請考慮使用 [SendGrid](https://docs.microsoft.com/azure/sendgrid-dotnet-how-to-send-email)，而不是連線到內部部署郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-118">For example, rather than connect to an on-premises mail server, consider using [SendGrid](https://docs.microsoft.com/azure/sendgrid-dotnet-how-to-send-email).</span></span>

### <a name="port-bindings"></a><span data-ttu-id="5a3f9-119">連接埠繫結</span><span class="sxs-lookup"><span data-stu-id="5a3f9-119">Port Bindings</span></span>

<span data-ttu-id="5a3f9-120">Azure App Service 支援連接埠 80 (適用於 HTTP) 和連接埠 443 (適用於 HTTPS 流量)。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-120">Azure App Service supports port 80 for HTTP and port 443 for HTTPS traffic.</span></span>

<span data-ttu-id="5a3f9-121">針對 WCF，支援下列繫結：</span><span class="sxs-lookup"><span data-stu-id="5a3f9-121">For WCF, the following bindings are supported:</span></span>

<span data-ttu-id="5a3f9-122">繫結</span><span class="sxs-lookup"><span data-stu-id="5a3f9-122">Binding</span></span> | <span data-ttu-id="5a3f9-123">備忘錄</span><span class="sxs-lookup"><span data-stu-id="5a3f9-123">Notes</span></span>
--------|--------
<span data-ttu-id="5a3f9-124">BasicHttp</span><span class="sxs-lookup"><span data-stu-id="5a3f9-124">BasicHttp</span></span> |
<span data-ttu-id="5a3f9-125">WSHttp</span><span class="sxs-lookup"><span data-stu-id="5a3f9-125">WSHttp</span></span> |
<span data-ttu-id="5a3f9-126">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="5a3f9-126">WSDualHttpBinding</span></span> | <span data-ttu-id="5a3f9-127">必須啟用 [Web 通訊端支援](https://docs.microsoft.com/azure/app-service/web-sites-configure)。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-127">[Web socket support](https://docs.microsoft.com/azure/app-service/web-sites-configure) must be enabled.</span></span>
<span data-ttu-id="5a3f9-128">NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="5a3f9-128">NetHttpBinding</span></span> | <span data-ttu-id="5a3f9-129">必須針對雙面合約啟用 [Web 通訊端支援](https://docs.microsoft.com/azure/app-service/web-sites-configure)。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-129">[Web socket support](https://docs.microsoft.com/azure/app-service/web-sites-configure) must be enabled for duplex contracts.</span></span>
<span data-ttu-id="5a3f9-130">NetHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="5a3f9-130">NetHttpsBinding</span></span> | <span data-ttu-id="5a3f9-131">必須針對雙面合約啟用 [Web 通訊端支援](https://docs.microsoft.com/azure/app-service/web-sites-configure)。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-131">[Web socket support](https://docs.microsoft.com/azure/app-service/web-sites-configure) must be enabled for duplex contracts.</span></span>
<span data-ttu-id="5a3f9-132">BasicHttpContextBinding</span><span class="sxs-lookup"><span data-stu-id="5a3f9-132">BasicHttpContextBinding</span></span> |
<span data-ttu-id="5a3f9-133">WebHttpBinding</span><span class="sxs-lookup"><span data-stu-id="5a3f9-133">WebHttpBinding</span></span> |
<span data-ttu-id="5a3f9-134">WSHttpContextBinding</span><span class="sxs-lookup"><span data-stu-id="5a3f9-134">WSHttpContextBinding</span></span> |

### <a name="authentication"></a><span data-ttu-id="5a3f9-135">驗證</span><span class="sxs-lookup"><span data-stu-id="5a3f9-135">Authentication</span></span>

<span data-ttu-id="5a3f9-136">Azure App Service 預設支援匿名驗證，在想要使用時支援表單驗證。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-136">Azure App Service supports anonymous authentication by default and Forms authentication when intended.</span></span> <span data-ttu-id="5a3f9-137">只有與 Azure Active Directory 和 ADFS 整合，才能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-137">Windows authentication can be used by integrating with Azure Active Directory and ADFS only.</span></span> <span data-ttu-id="5a3f9-138">[深入了解如何整合您的內部部署目錄與 Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-138">[Learn more about how to integrate your on-premises directories with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).</span></span>

### <a name="assemblies-in-the-gac-global-assembly-cache"></a><span data-ttu-id="5a3f9-139">GAC (全域組件快取) 中的組件</span><span class="sxs-lookup"><span data-stu-id="5a3f9-139">Assemblies in the GAC (Global Assembly Cache)</span></span>

<span data-ttu-id="5a3f9-140">不支援此做法。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-140">This isn't supported.</span></span> <span data-ttu-id="5a3f9-141">請考慮將必要的元件複製到應用程式的*\bin*資料夾。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-141">Consider copying required assemblies to the app's *\bin* folder.</span></span> <span data-ttu-id="5a3f9-142">無法使用安裝在伺服器上的自訂 *.msi*檔案（例如，PDF 產生器）。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-142">Custom *.msi* files installed on the server (for example, PDF generators) cannot be used.</span></span>

### <a name="iis-settings"></a><span data-ttu-id="5a3f9-143">IIS 設定</span><span class="sxs-lookup"><span data-stu-id="5a3f9-143">IIS settings</span></span>

<span data-ttu-id="5a3f9-144">傳統上透過應用程式中 applicationHost.config 設定的所有項目現在皆可透過 Azure 入口網站設定。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-144">Everything traditionally configured via applicationHost.config in your application can now be configured through the Azure portal.</span></span> <span data-ttu-id="5a3f9-145">這適用于 AppPool 位、啟用/停用 Websocket、受管理的管線版本、.NET Framework 版本（2.0/4.0）等等。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-145">This applies to AppPool bitness, enable/disable WebSockets, managed pipeline version, .NET Framework version (2.0/4.0), and so on.</span></span> <span data-ttu-id="5a3f9-146">若要修改[應用程式設定](https://docs.microsoft.com/azure/app-service/web-sites-configure)，瀏覽至 [Azure 入口網站](https://portal.azure.com)，開啟 Web 應用程式刀鋒視窗，然後選取 [應用程式設定]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-146">To modify your [application settings](https://docs.microsoft.com/azure/app-service/web-sites-configure), navigate to the [Azure portal](https://portal.azure.com), open the blade for your web app, and then select the **Application Settings** tab.</span></span>

#### <a name="iis5-compatibility-mode"></a><span data-ttu-id="5a3f9-147">IIS5 相容性模式</span><span class="sxs-lookup"><span data-stu-id="5a3f9-147">IIS5 Compatibility Mode</span></span>

<span data-ttu-id="5a3f9-148">不支援 IIS5 相容性模式。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-148">IIS5 Compatibility Mode is not supported.</span></span> <span data-ttu-id="5a3f9-149">在 Azure App Service 中，每個 web 應用程式和其下的所有應用程式會在相同的工作者進程中，使用一組特定的[應用程式](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc735247(v=ws.10))集區來執行。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-149">In Azure App Service, each web app and all of the applications under it run in the same worker process with a specific set of [application pools](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc735247(v=ws.10)).</span></span>

#### <a name="iis7-schema-compliance"></a><span data-ttu-id="5a3f9-150">IIS7+ 結構描述合規性</span><span class="sxs-lookup"><span data-stu-id="5a3f9-150">IIS7+ schema compliance</span></span>

<span data-ttu-id="5a3f9-151">部分元素和屬性未在 Azure App Service IIS 結構描述中定義。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-151">Some elements and attributes are not defined in the Azure App Service IIS schema.</span></span> <span data-ttu-id="5a3f9-152">如果您遇到問題，請考慮使用 [XDT 轉換](https://azure.microsoft.com/documentation/articles/web-sites-transform-extend/)。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-152">If you encounter issues, consider using [XDT transforms](https://azure.microsoft.com/documentation/articles/web-sites-transform-extend/).</span></span>

#### <a name="single-application-pool-per-site"></a><span data-ttu-id="5a3f9-153">每個網站單一應用程式集區</span><span class="sxs-lookup"><span data-stu-id="5a3f9-153">Single application pool per site</span></span>

<span data-ttu-id="5a3f9-154">在 Azure App Service 中，每個 web 應用程式和其下的所有應用程式都會在相同的應用程式集區中執行。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-154">In Azure App Service, each web app and all of the applications under it run in the same application pool.</span></span> <span data-ttu-id="5a3f9-155">請考慮建立具有一般設定的單一應用程式集區，或為每個應用程式建立個別的 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-155">Consider establishing a single application pool with common settings or creating a separate web app for each application.</span></span>

### <a name="com-and-com-components"></a><span data-ttu-id="5a3f9-156">COM 和 COM+ 元件</span><span class="sxs-lookup"><span data-stu-id="5a3f9-156">COM and COM+ components</span></span>

<span data-ttu-id="5a3f9-157">Azure App Service 不允許在平台上註冊 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-157">Azure App Service does not allow the registration of COM components on the platform.</span></span> <span data-ttu-id="5a3f9-158">如果您的應用程式使用任何 COM 元件，則需要在 managed 程式碼中改寫，並與網站或應用程式一起部署。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-158">If your app makes use of any COM components, these need to be rewritten in managed code and deployed with the site or application.</span></span>

### <a name="physical-directories"></a><span data-ttu-id="5a3f9-159">實體目錄</span><span class="sxs-lookup"><span data-stu-id="5a3f9-159">Physical directories</span></span>

<span data-ttu-id="5a3f9-160">Azure App Service 不允許實體磁碟存取。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-160">Azure App Service does not allow physical drive access.</span></span> <span data-ttu-id="5a3f9-161">您可能需要使用[Azure 檔案儲存體](https://docs.microsoft.com/azure/storage/files/storage-files-introduction)透過 SMB 存取檔案。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-161">You may need to use [Azure Files](https://docs.microsoft.com/azure/storage/files/storage-files-introduction) to access files via SMB.</span></span> <span data-ttu-id="5a3f9-162">[Azure Blob 儲存體](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction)可以儲存檔案，以供透過 HTTPS 存取。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-162">[Azure Blob Storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) can store files for access via HTTPS.</span></span>

### <a name="isapi-filters"></a><span data-ttu-id="5a3f9-163">ISAPI 篩選器</span><span class="sxs-lookup"><span data-stu-id="5a3f9-163">ISAPI filters</span></span>

<span data-ttu-id="5a3f9-164">Azure App Service 支援使用 ISAPI 篩選；不過，ISAPI DLL 必須部署到您的網站，並透過 web.config 註冊。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-164">Azure App Service can support the use of ISAPI Filters, however, the ISAPI DLL must be deployed with your site and registered via web.config.</span></span>

### <a name="https-bindings-and-ssl"></a><span data-ttu-id="5a3f9-165">HTTPS 繫結和 SSL</span><span class="sxs-lookup"><span data-stu-id="5a3f9-165">HTTPS bindings and SSL</span></span>

<span data-ttu-id="5a3f9-166">HTTPS 系結不會遷移，也不會與您的網站相關聯的 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-166">HTTPS bindings are not migrated, nor are the SSL certificates associated with your web sites.</span></span> <span data-ttu-id="5a3f9-167">但是，在網站移轉完成之後，[可以手動上傳 SSL 憑證](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-ssl)。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-167">[SSL certificates can be manually uploaded](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-ssl) after site migration is completed, however.</span></span>

### <a name="sharepoint-and-frontpage"></a><span data-ttu-id="5a3f9-168">SharePoint 和 FrontPage</span><span class="sxs-lookup"><span data-stu-id="5a3f9-168">SharePoint and FrontPage</span></span>

<span data-ttu-id="5a3f9-169">不支援 SharePoint 和 FrontPage Server Extensions (FPSE)。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-169">SharePoint and FrontPage Server Extensions (FPSE) are not supported.</span></span>

### <a name="web-site-size"></a><span data-ttu-id="5a3f9-170">網站大小</span><span class="sxs-lookup"><span data-stu-id="5a3f9-170">Web site size</span></span>

<span data-ttu-id="5a3f9-171">可用網站具有 1 GB 內容的大小限制。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-171">Free sites have a size limit of 1 GB of content.</span></span> <span data-ttu-id="5a3f9-172">如果您的網站大於 1 GB，您必須升級為付費 SKU。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-172">If your site is greater than 1 GB, you must upgrade to a paid SKU.</span></span> <span data-ttu-id="5a3f9-173">請參閱 [App Service 定價](https://azure.microsoft.com/pricing/details/app-service/windows/)。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-173">See [App Service pricing](https://azure.microsoft.com/pricing/details/app-service/windows/).</span></span>

### <a name="database-size"></a><span data-ttu-id="5a3f9-174">資料庫大小</span><span class="sxs-lookup"><span data-stu-id="5a3f9-174">Database size</span></span>

<span data-ttu-id="5a3f9-175">針對 SQL Server 資料庫，請參閱目前的 [SQL Database 定價](https://azure.microsoft.com/pricing/details/sql-database)。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-175">For SQL Server databases, please check the current [SQL Database pricing](https://azure.microsoft.com/pricing/details/sql-database).</span></span>

### <a name="azure-active-directory-aad-integration"></a><span data-ttu-id="5a3f9-176">Azure Active Directory (AAD) 整合</span><span class="sxs-lookup"><span data-stu-id="5a3f9-176">Azure Active Directory (AAD) integration</span></span>

<span data-ttu-id="5a3f9-177">AAD 無法使用免費應用程式。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-177">AAD does not work with free apps.</span></span> <span data-ttu-id="5a3f9-178">若要使用 AAD，您必須升級應用程式 SKU。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-178">To use AAD, you must upgrade the app SKU.</span></span> <span data-ttu-id="5a3f9-179">請參閱 [App Service 定價](https://azure.microsoft.com/pricing/details/app-service/windows/)。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-179">See [App Service pricing](https://azure.microsoft.com/pricing/details/app-service/windows/).</span></span>

### <a name="monitoring-and-diagnostics"></a><span data-ttu-id="5a3f9-180">監視和診斷</span><span class="sxs-lookup"><span data-stu-id="5a3f9-180">Monitoring and diagnostics</span></span>

<span data-ttu-id="5a3f9-181">您目前的監控和診斷內部部署解決方案無法在雲端中運作。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-181">Your current on-premises solutions for monitoring and diagnostics are unlikely to work in the cloud.</span></span> <span data-ttu-id="5a3f9-182">不過，Azure 提供記錄、監控和診斷工具，以便識別及偵錯 Web 應用程式的問題。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-182">However, Azure provides tools for logging, monitoring, and diagnostics so that you can identify and debug issues with web apps.</span></span> <span data-ttu-id="5a3f9-183">您可以輕鬆地在設定中啟用 Web 應用程式診斷，且可以檢視 Azure Application Insights 中所記的記錄。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-183">You can easily enable diagnostics for your web app in its configuration, and you can view the logs recorded in Azure Application Insights.</span></span> <span data-ttu-id="5a3f9-184">[深入了解啟用 Web 應用程式的診斷記錄](https://docs.microsoft.com/azure/app-service/web-sites-enable-diagnostic-log)。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-184">[Learn more about enabling diagnostics logging for web apps](https://docs.microsoft.com/azure/app-service/web-sites-enable-diagnostic-log).</span></span>

### <a name="connection-strings-and-application-settings"></a><span data-ttu-id="5a3f9-185">連接字串和應用程式設定</span><span class="sxs-lookup"><span data-stu-id="5a3f9-185">Connection strings and application settings</span></span>

<span data-ttu-id="5a3f9-186">請考慮使用 [Azure KeyVault](https://docs.microsoft.com/azure/key-vault/)，這項服務可以安全地儲存應用程式中所使用的敏感資訊。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-186">Consider using [Azure KeyVault](https://docs.microsoft.com/azure/key-vault/), a service that securely stores sensitive information used in your application.</span></span> <span data-ttu-id="5a3f9-187">或者，您可以將此資料儲存為 App Service 設定。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-187">Alternatively, you can store this data as an App Service setting.</span></span>

### <a name="dns"></a><span data-ttu-id="5a3f9-188">DNS</span><span class="sxs-lookup"><span data-stu-id="5a3f9-188">DNS</span></span>

<span data-ttu-id="5a3f9-189">您可能需要根據應用程式需求更新 DNS 設定。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-189">You may need to update DNS configurations based on the requirements of your application.</span></span> <span data-ttu-id="5a3f9-190">這些 DNS 設定可在 App Service 的[自訂網域設定](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-domain)中進行設定。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-190">These DNS settings can be configured in the App Service [custom domain settings](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-domain).</span></span>

## <a name="azure-app-service-with-windows-containers"></a><span data-ttu-id="5a3f9-191">Azure App Service 與 Windows 容器</span><span class="sxs-lookup"><span data-stu-id="5a3f9-191">Azure App Service with Windows Containers</span></span>

<span data-ttu-id="5a3f9-192">如果您的應用程式無法直接遷移至 App Service，請考慮使用 Windows 容器的 App Service，它可以使用 GAC、COM 元件、MSI 並完整存取 .NET FX API、DirectX 等等。</span><span class="sxs-lookup"><span data-stu-id="5a3f9-192">If your app cannot be migrated directly to App Service, consider App Service using Windows Containers, which enables usage of the GAC, COM components, MSIs, full access to .NET FX APIs, DirectX, and more.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a3f9-193">請參閱</span><span class="sxs-lookup"><span data-stu-id="5a3f9-193">See also</span></span>

* [<span data-ttu-id="5a3f9-194">如何判斷您的應用程式是否符合 App Service</span><span class="sxs-lookup"><span data-stu-id="5a3f9-194">How to determine if your app qualifies for App Service</span></span>](https://appmigration.microsoft.com/)
* [<span data-ttu-id="5a3f9-195">將您的資料庫移至雲端</span><span class="sxs-lookup"><span data-stu-id="5a3f9-195">Moving your database to the cloud</span></span>](sql.md)
* [<span data-ttu-id="5a3f9-196">Azure web 應用程式沙箱詳細資料和限制</span><span class="sxs-lookup"><span data-stu-id="5a3f9-196">Azure web app sandbox details and restrictions</span></span>](https://github.com/projectkudu/kudu/wiki/Azure-Web-App-sandbox)

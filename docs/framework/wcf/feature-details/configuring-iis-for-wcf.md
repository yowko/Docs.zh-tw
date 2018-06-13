---
title: 設定 Internet Information Services 7.0 for Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 3e34f46fbf3ccf12c6a89a7cac96143965d958d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491712"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a><span data-ttu-id="a172a-102">設定 Internet Information Services 7.0 for Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a172a-102">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>
<span data-ttu-id="a172a-103">Internet Information Services (IIS) 7.0 具有模組化的設計，可以讓您選擇性地安裝所需的元件。</span><span class="sxs-lookup"><span data-stu-id="a172a-103">Internet Information Services (IIS) 7.0 has a modular design that allows you to selectively install components that are required.</span></span> <span data-ttu-id="a172a-104">這項設計是以 [!INCLUDE[wv](../../../../includes/wv-md.md)]中引進的新資訊清單驅動元件化技術為基礎。</span><span class="sxs-lookup"><span data-stu-id="a172a-104">This design is based on the new manifest-driven componentization technology introduced in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="a172a-105">[!INCLUDE[iisver](../../../../includes/iisver-md.md)] 有超過 40 項可以個別安裝的獨立功能元件。</span><span class="sxs-lookup"><span data-stu-id="a172a-105">There are more than 40 standalone feature components of [!INCLUDE[iisver](../../../../includes/iisver-md.md)] that can be installed independently.</span></span> <span data-ttu-id="a172a-106">這讓 IT 專業人員能夠輕鬆地依其需要自訂安裝。</span><span class="sxs-lookup"><span data-stu-id="a172a-106">This allows IT professionals to easily customize the installation as required.</span></span> <span data-ttu-id="a172a-107">本主題討論如何設定[!INCLUDE[iisver](../../../../includes/iisver-md.md)]的使用與 Windows Communication Foundation (WCF)，並判斷所需的元件。</span><span class="sxs-lookup"><span data-stu-id="a172a-107">This topic discusses how to configure [!INCLUDE[iisver](../../../../includes/iisver-md.md)] for use with Windows Communication Foundation (WCF) and determine which components are required.</span></span>  
  
## <a name="minimal-installation-installing-was"></a><span data-ttu-id="a172a-108">基本安裝：安裝 WAS</span><span class="sxs-lookup"><span data-stu-id="a172a-108">Minimal Installation: Installing WAS</span></span>  
 <span data-ttu-id="a172a-109">完整 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 套件的基本安裝是安裝 Windows Process Activation Service (WAS)。</span><span class="sxs-lookup"><span data-stu-id="a172a-109">The minimal installation of the whole [!INCLUDE[iisver](../../../../includes/iisver-md.md)] package is to install the Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="a172a-110">WAS 是獨立的功能，而且是唯一能在所有 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 作業系統 (Home Basic、Home Premium、Business、Ultimate 及 Enterprise) 上提供的 [!INCLUDE[wv](../../../../includes/wv-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="a172a-110">WAS is a standalone feature and it is the only feature from the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] that is available for all [!INCLUDE[wv](../../../../includes/wv-md.md)] operating systems (Home Basic, Home Premium, Business, and Ultimate and Enterprise).</span></span>  
  
 <span data-ttu-id="a172a-111">從 [控制台] 中按一下**程式**，然後按一下 [**開啟或關閉 Windows 功能**] 下**程式和功能**，WAS 元件隨即顯示清單中，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="a172a-111">From the Control Panel, click **Programs** and then click **Turn Windows features on or off** which is listed under **Programs and Features**, the WAS component is shown in the list as in the following illustration.</span></span>  
  
 <span data-ttu-id="a172a-112">![功能開啟或關閉對話方塊](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span><span class="sxs-lookup"><span data-stu-id="a172a-112">![Turn Features On or Off Dialog](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span></span>  
  
 <span data-ttu-id="a172a-113">這項功能具有下列子元件：</span><span class="sxs-lookup"><span data-stu-id="a172a-113">This feature has the following sub-components:</span></span>  
  
-   <span data-ttu-id="a172a-114">.NET 環境</span><span class="sxs-lookup"><span data-stu-id="a172a-114">.NET Environment</span></span>  
  
-   <span data-ttu-id="a172a-115">組態 API</span><span class="sxs-lookup"><span data-stu-id="a172a-115">Configuration APIs</span></span>  
  
-   <span data-ttu-id="a172a-116">處理序模型</span><span class="sxs-lookup"><span data-stu-id="a172a-116">Process Model</span></span>  
  
 <span data-ttu-id="a172a-117">如果您選取 WAS 的根節點僅**處理序模型**預設會核取子節點。</span><span class="sxs-lookup"><span data-stu-id="a172a-117">If you select the root node of WAS, only the **Process Model** sub-node is checked by default.</span></span> <span data-ttu-id="a172a-118">請注意，進行這項安裝時只會安裝 WAS，因為此時不支援 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a172a-118">Please note that with this installation you are only installing WAS, because there is no support for a Web server.</span></span>  
  
 <span data-ttu-id="a172a-119">若要讓 WCF 或任何[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]應用程式運作，請檢查 **.NET 環境**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a172a-119">To make WCF or any [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application to work, check the **.NET Environment** checkbox.</span></span> <span data-ttu-id="a172a-120">這表示所有的 WAS 元件都需要讓 WCF 和[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="a172a-120">This means that all of WAS components are required to make WCF and [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] to work well.</span></span> <span data-ttu-id="a172a-121">一旦您安裝任何其中一個上述元件，這些應用程式便會自動核取。</span><span class="sxs-lookup"><span data-stu-id="a172a-121">These are automatically checked once you install any of those components.</span></span>  
  
## <a name="iis-70-default-installation"></a><span data-ttu-id="a172a-122">IIS 7.0：預設安裝</span><span class="sxs-lookup"><span data-stu-id="a172a-122">IIS 7.0: Default Installation</span></span>  
 <span data-ttu-id="a172a-123">藉由檢查**Internet Information Services**功能，某些子節點會自動核取下圖所示。</span><span class="sxs-lookup"><span data-stu-id="a172a-123">By checking the **Internet Information Services** feature, some of the sub-nodes are automatically checked as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="a172a-124">![IIS 7.0 功能的預設設定](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span><span class="sxs-lookup"><span data-stu-id="a172a-124">![Default settings for IIS 7.0 features](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span></span>  
  
 <span data-ttu-id="a172a-125">這是 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 的預設安裝。</span><span class="sxs-lookup"><span data-stu-id="a172a-125">This is the default installation of [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="a172a-126">運用這項安裝，您可以使用 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 來提供靜態內容的服務 (例如 HTML 頁面和其他內容)。</span><span class="sxs-lookup"><span data-stu-id="a172a-126">With this installation, you can use [!INCLUDE[iisver](../../../../includes/iisver-md.md)] to service static content (such as HTML pages and other content).</span></span> <span data-ttu-id="a172a-127">不過，您無法執行[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]或 CGI 應用程式或裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="a172a-127">However, you cannot run [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] or CGI applications or host WCF services.</span></span>  
  
## <a name="iis-70-installation-with-aspnet-support"></a><span data-ttu-id="a172a-128">IIS 7.0：具有 ASP.NET 支援的安裝</span><span class="sxs-lookup"><span data-stu-id="a172a-128">IIS 7.0: Installation with ASP.NET Support</span></span>  
 <span data-ttu-id="a172a-129">您必須安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 才能讓 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 在 IIS 7.0 上運作。</span><span class="sxs-lookup"><span data-stu-id="a172a-129">You must install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] to make [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] work on IIS 7.0.</span></span> <span data-ttu-id="a172a-130">檢查後**ASP.NET**，您的畫面應該看起來像下圖。</span><span class="sxs-lookup"><span data-stu-id="a172a-130">After checking **ASP.NET**, your screen should look like the following illustration.</span></span>  
  
 <span data-ttu-id="a172a-131">![Asp.NET 必要設定](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span><span class="sxs-lookup"><span data-stu-id="a172a-131">![Asp.NET required settings](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span></span>  
  
 <span data-ttu-id="a172a-132">這是這兩個 WCF 環境的最小和[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]應用程式運作[!INCLUDE[iisver](../../../../includes/iisver-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a172a-132">This is the minimal environment for both WCF and [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] applications to work in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span>  
  
## <a name="iis-70-installation-with-iis-60-compatibility-components"></a><span data-ttu-id="a172a-133">IIS 7.0：具有 IIS 6.0 相容性元件的安裝</span><span class="sxs-lookup"><span data-stu-id="a172a-133">IIS 7.0: Installation with IIS 6.0 Compatibility Components</span></span>  
 <span data-ttu-id="a172a-134">安裝時[!INCLUDE[iisver](../../../../includes/iisver-md.md)]Visual Studio 2005 或某些其他自動化指令碼或工具 （例如 Adsutil.vbs) 設定使用的虛擬應用程式的系統上[!INCLUDE[iis601](../../../../includes/iis601-md.md)]Metabase API，請確定[!INCLUDE[iis601](../../../../includes/iis601-md.md)] **指令碼工具**。</span><span class="sxs-lookup"><span data-stu-id="a172a-134">When installing [!INCLUDE[iisver](../../../../includes/iisver-md.md)] on a system with Visual Studio 2005 or some other automation scripts or tools (such as Adsutil.vbs) that configure virtual applications that use [!INCLUDE[iis601](../../../../includes/iis601-md.md)] Metabase API, ensure that you check the [!INCLUDE[iis601](../../../../includes/iis601-md.md)]**Scripting Tools**.</span></span> <span data-ttu-id="a172a-135">這會自動檢查的其他子節點[!INCLUDE[iis601](../../../../includes/iis601-md.md)]**管理相容性**。</span><span class="sxs-lookup"><span data-stu-id="a172a-135">This automatically checks the other sub-nodes of [!INCLUDE[iis601](../../../../includes/iis601-md.md)]**Management Compatibility**.</span></span> <span data-ttu-id="a172a-136">下圖顯示完成此步驟之後的畫面。</span><span class="sxs-lookup"><span data-stu-id="a172a-136">The following illustration shows the screen after this is done.</span></span>  
  
 <span data-ttu-id="a172a-137">![IIS 6.0 管理相容性設定](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span><span class="sxs-lookup"><span data-stu-id="a172a-137">![IIS 6.0 Management Compatibility Settings](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span></span>  
  
 <span data-ttu-id="a172a-138">透過這項安裝，您可以使用所需的所有[!INCLUDE[iisver](../../../../includes/iisver-md.md)]， [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 上提供範例和 WCF 的功能。</span><span class="sxs-lookup"><span data-stu-id="a172a-138">With this installation, you have everything required to use [!INCLUDE[iisver](../../../../includes/iisver-md.md)], [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] and WCF features and samples available on the Web.</span></span>  
  
## <a name="request-limits"></a><span data-ttu-id="a172a-139">要求限制</span><span class="sxs-lookup"><span data-stu-id="a172a-139">Request Limits</span></span>  
 <span data-ttu-id="a172a-140">在具有 IIS 7 的 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上，`maxUri` 和 `maxQueryStringSize` 設定的預設值已經變更。</span><span class="sxs-lookup"><span data-stu-id="a172a-140">On [!INCLUDE[wv](../../../../includes/wv-md.md)] with IIS 7 the default value of the `maxUri` and `maxQueryStringSize` settings have been changed.</span></span> <span data-ttu-id="a172a-141">根據預設，IIS 7.0 中的要求篩選允許 URL 長度為 4096 個字元，查詢字串長度為 2048 個字元。</span><span class="sxs-lookup"><span data-stu-id="a172a-141">By default, request filtering in IIS 7.0 allows a URL length of 4096 characters and a query string length of 2048 characters.</span></span> <span data-ttu-id="a172a-142">若要變更這些預設值，請將下列 XML 加入至您的 App.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="a172a-142">To change these defaults add the following XML to your App.config file.</span></span>  
  
 `<system.webServer>`  
  
 `<security>`  
  
 `<requestFiltering>`  
  
 `<requestLimits maxUrl="8192" maxQueryString="8192" />`  
  
 `</requestFiltering>`  
  
 `</security>`  
  
 `</system.webServer>`  
  
## <a name="see-also"></a><span data-ttu-id="a172a-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a172a-143">See Also</span></span>  
 [<span data-ttu-id="a172a-144">WAS 啟用架構</span><span class="sxs-lookup"><span data-stu-id="a172a-144">WAS Activation Architecture</span></span>](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)  
 [<span data-ttu-id="a172a-145">設定用於 WCF 的 WAS</span><span class="sxs-lookup"><span data-stu-id="a172a-145">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [<span data-ttu-id="a172a-146">如何：安裝和設定 WCF 啟用元件</span><span class="sxs-lookup"><span data-stu-id="a172a-146">How to: Install and Configure WCF Activation Components</span></span>](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
 [<span data-ttu-id="a172a-147">Windows Server App Fabric 裝載功能</span><span class="sxs-lookup"><span data-stu-id="a172a-147">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)

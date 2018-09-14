---
title: 設定 Internet Information Services 7.0 for Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 13fd068f7a058a0fbf4e15fc99a8de91671fb2d5
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521349"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a><span data-ttu-id="d5f71-102">設定 Internet Information Services 7.0 for Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d5f71-102">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>

<span data-ttu-id="d5f71-103">Internet Information Services (IIS) 7.0 具有模組化的設計，可以讓您選擇性地安裝所需的元件。</span><span class="sxs-lookup"><span data-stu-id="d5f71-103">Internet Information Services (IIS) 7.0 has a modular design that allows you to selectively install components that are required.</span></span> <span data-ttu-id="d5f71-104">這項設計是以 [!INCLUDE[wv](../../../../includes/wv-md.md)]中引進的新資訊清單驅動元件化技術為基礎。</span><span class="sxs-lookup"><span data-stu-id="d5f71-104">This design is based on the new manifest-driven componentization technology introduced in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="d5f71-105">有 40 個以上的獨立功能元件，可獨立安裝的 IIS 7.0。</span><span class="sxs-lookup"><span data-stu-id="d5f71-105">There are more than 40 standalone feature components of IIS 7.0 that can be installed independently.</span></span> <span data-ttu-id="d5f71-106">這讓 IT 專業人員能夠輕鬆地依其需要自訂安裝。</span><span class="sxs-lookup"><span data-stu-id="d5f71-106">This allows IT professionals to easily customize the installation as required.</span></span> <span data-ttu-id="d5f71-107">本主題討論如何設定 IIS 7.0 使用與 Windows Communication Foundation (WCF)，並判斷需要哪些元件。</span><span class="sxs-lookup"><span data-stu-id="d5f71-107">This topic discusses how to configure IIS 7.0 for use with Windows Communication Foundation (WCF) and determine which components are required.</span></span>

## <a name="minimal-installation-installing-was"></a><span data-ttu-id="d5f71-108">基本安裝：安裝 WAS</span><span class="sxs-lookup"><span data-stu-id="d5f71-108">Minimal Installation: Installing WAS</span></span>
 <span data-ttu-id="d5f71-109">整個 IIS 7.0 封裝的基本安裝是安裝 Windows Process Activation Service (WAS)。</span><span class="sxs-lookup"><span data-stu-id="d5f71-109">The minimal installation of the whole IIS 7.0 package is to install the Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="d5f71-110">已是獨立功能，它是唯一的功能，可供所有 IIS 7.0[!INCLUDE[wv](../../../../includes/wv-md.md)]作業系統 （Home Basic、 Home Premium、 Business 和 Ultimate 和 Enterprise）。</span><span class="sxs-lookup"><span data-stu-id="d5f71-110">WAS is a standalone feature and it is the only feature from the IIS 7.0 that is available for all [!INCLUDE[wv](../../../../includes/wv-md.md)] operating systems (Home Basic, Home Premium, Business, and Ultimate and Enterprise).</span></span>

 <span data-ttu-id="d5f71-111">從 控制台 中按一下**程式**，然後按一下**開啟 Windows 功能開啟或關閉** 下**程式和功能**，WAS 元件所示如下列圖所示的清單。</span><span class="sxs-lookup"><span data-stu-id="d5f71-111">From the Control Panel, click **Programs** and then click **Turn Windows features on or off** which is listed under **Programs and Features**, the WAS component is shown in the list as in the following illustration.</span></span>

 <span data-ttu-id="d5f71-112">![功能開啟或關閉對話方塊](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span><span class="sxs-lookup"><span data-stu-id="d5f71-112">![Turn Features On or Off Dialog](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span></span>

 <span data-ttu-id="d5f71-113">這項功能具有下列子元件：</span><span class="sxs-lookup"><span data-stu-id="d5f71-113">This feature has the following sub-components:</span></span>

-   <span data-ttu-id="d5f71-114">.NET 環境</span><span class="sxs-lookup"><span data-stu-id="d5f71-114">.NET Environment</span></span>

-   <span data-ttu-id="d5f71-115">組態 API</span><span class="sxs-lookup"><span data-stu-id="d5f71-115">Configuration APIs</span></span>

-   <span data-ttu-id="d5f71-116">處理序模型</span><span class="sxs-lookup"><span data-stu-id="d5f71-116">Process Model</span></span>

 <span data-ttu-id="d5f71-117">如果您選取根節點的 WAS，只有**處理序模型**子節點依預設會勾選。</span><span class="sxs-lookup"><span data-stu-id="d5f71-117">If you select the root node of WAS, only the **Process Model** sub-node is checked by default.</span></span> <span data-ttu-id="d5f71-118">請注意，進行這項安裝時只會安裝 WAS，因為此時不支援 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d5f71-118">Please note that with this installation you are only installing WAS, because there is no support for a Web server.</span></span>

 <span data-ttu-id="d5f71-119">若要讓 WCF 或任何 ASP.NET 應用程式工作，請檢查 **.NET 環境**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d5f71-119">To make WCF or any ASP.NET application work, check the **.NET Environment** checkbox.</span></span> <span data-ttu-id="d5f71-120">這表示所有的 WAS 元件都需要進行 WCF 和 ASP.NET 無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="d5f71-120">This means that all of WAS components are required to make WCF and ASP.NET to work well.</span></span> <span data-ttu-id="d5f71-121">一旦您安裝任何其中一個上述元件，這些應用程式便會自動核取。</span><span class="sxs-lookup"><span data-stu-id="d5f71-121">These are automatically checked once you install any of those components.</span></span>

## <a name="iis-70-default-installation"></a><span data-ttu-id="d5f71-122">IIS 7.0：預設安裝</span><span class="sxs-lookup"><span data-stu-id="d5f71-122">IIS 7.0: Default Installation</span></span>
 <span data-ttu-id="d5f71-123">藉由檢查**Internet Information Services**如下圖所示，會自動檢查功能，某些子節點。</span><span class="sxs-lookup"><span data-stu-id="d5f71-123">By checking the **Internet Information Services** feature, some of the sub-nodes are automatically checked as shown in the following illustration.</span></span>

 <span data-ttu-id="d5f71-124">![IIS 7.0 功能的預設值](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span><span class="sxs-lookup"><span data-stu-id="d5f71-124">![Default settings for IIS 7.0 features](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span></span>

 <span data-ttu-id="d5f71-125">這是 IIS 7.0 的預設安裝。</span><span class="sxs-lookup"><span data-stu-id="d5f71-125">This is the default installation of IIS 7.0.</span></span> <span data-ttu-id="d5f71-126">這項安裝，您可以使用 IIS 7.0 來服務靜態內容 （例如 HTML 網頁和其他內容）。</span><span class="sxs-lookup"><span data-stu-id="d5f71-126">With this installation, you can use IIS 7.0 to service static content (such as HTML pages and other content).</span></span> <span data-ttu-id="d5f71-127">不過，您無法執行 ASP.NET 或 CGI 應用程式或裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="d5f71-127">However, you cannot run ASP.NET or CGI applications or host WCF services.</span></span>

## <a name="iis-70-installation-with-aspnet-support"></a><span data-ttu-id="d5f71-128">IIS 7.0：具有 ASP.NET 支援的安裝</span><span class="sxs-lookup"><span data-stu-id="d5f71-128">IIS 7.0: Installation with ASP.NET Support</span></span>
 <span data-ttu-id="d5f71-129">您必須安裝 ASP.NET，讓 ASP.NET 在 IIS 7.0 上運作。</span><span class="sxs-lookup"><span data-stu-id="d5f71-129">You must install ASP.NET to make ASP.NET work on IIS 7.0.</span></span> <span data-ttu-id="d5f71-130">檢查後**ASP.NET**，您的畫面應該看起來類似下圖。</span><span class="sxs-lookup"><span data-stu-id="d5f71-130">After checking **ASP.NET**, your screen should look like the following illustration.</span></span>

 <span data-ttu-id="d5f71-131">![Asp.NET 必要設定](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span><span class="sxs-lookup"><span data-stu-id="d5f71-131">![Asp.NET required settings](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span></span>

 <span data-ttu-id="d5f71-132">這是最小的環境，讓 IIS 7.0 中運作的 WCF 和 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d5f71-132">This is the minimal environment for both WCF and ASP.NET applications to work in IIS 7.0.</span></span>

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a><span data-ttu-id="d5f71-133">IIS 7.0：具有 IIS 6.0 相容性元件的安裝</span><span class="sxs-lookup"><span data-stu-id="d5f71-133">IIS 7.0: Installation with IIS 6.0 Compatibility Components</span></span>
 <span data-ttu-id="d5f71-134">當 Visual Studio 2005 或其他自動化指令碼或設定使用 IIS 6.0 Metabase API 的虛擬應用程式的工具 （例如 Adsutil.vbs) 的系統上安裝 IIS 7.0，請確定您檢查 IIS 6.0**指令碼工具**.</span><span class="sxs-lookup"><span data-stu-id="d5f71-134">When installing IIS 7.0 on a system with Visual Studio 2005 or some other automation scripts or tools (such as Adsutil.vbs) that configure virtual applications that use IIS 6.0 Metabase API, ensure that you check the IIS 6.0 **Scripting Tools**.</span></span> <span data-ttu-id="d5f71-135">這會自動檢查 IIS 6.0 的其他子節點**管理相容性**。</span><span class="sxs-lookup"><span data-stu-id="d5f71-135">This automatically checks the other sub-nodes of IIS 6.0 **Management Compatibility**.</span></span> <span data-ttu-id="d5f71-136">這麼做之後下, 圖顯示的畫面：</span><span class="sxs-lookup"><span data-stu-id="d5f71-136">The following illustration shows the screen after this is done:</span></span>

 <span data-ttu-id="d5f71-137">![IIS 6.0 管理相容性設定](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span><span class="sxs-lookup"><span data-stu-id="d5f71-137">![IIS 6.0 Management Compatibility Settings](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span></span>

 <span data-ttu-id="d5f71-138">此安裝中，您可以使用網頁上的 IIS 7.0、 ASP.NET 和 WCF 的功能和可用的範例所需的所有項目。</span><span class="sxs-lookup"><span data-stu-id="d5f71-138">With this installation, you have everything required to use IIS 7.0, ASP.NET and WCF features and samples available on the Web.</span></span>

## <a name="request-limits"></a><span data-ttu-id="d5f71-139">要求限制</span><span class="sxs-lookup"><span data-stu-id="d5f71-139">Request Limits</span></span>
 <span data-ttu-id="d5f71-140">在具有 IIS 7 的 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上，`maxUri` 和 `maxQueryStringSize` 設定的預設值已經變更。</span><span class="sxs-lookup"><span data-stu-id="d5f71-140">On [!INCLUDE[wv](../../../../includes/wv-md.md)] with IIS 7 the default value of the `maxUri` and `maxQueryStringSize` settings have been changed.</span></span> <span data-ttu-id="d5f71-141">根據預設，IIS 7.0 中的要求篩選允許 URL 長度為 4096 個字元，查詢字串長度為 2048 個字元。</span><span class="sxs-lookup"><span data-stu-id="d5f71-141">By default, request filtering in IIS 7.0 allows a URL length of 4096 characters and a query string length of 2048 characters.</span></span> <span data-ttu-id="d5f71-142">若要變更這些預設值，請將下列 XML 加入至您的 App.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="d5f71-142">To change these defaults add the following XML to your App.config file.</span></span>

 `<system.webServer>`

 `<security>`

 `<requestFiltering>`

 `<requestLimits maxUrl="8192" maxQueryString="8192" />`

 `</requestFiltering>`

 `</security>`

 `</system.webServer>`

## <a name="see-also"></a><span data-ttu-id="d5f71-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5f71-143">See Also</span></span>

- [<span data-ttu-id="d5f71-144">WAS 啟用架構</span><span class="sxs-lookup"><span data-stu-id="d5f71-144">WAS Activation Architecture</span></span>](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [<span data-ttu-id="d5f71-145">設定用於 WCF 的 WAS</span><span class="sxs-lookup"><span data-stu-id="d5f71-145">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [<span data-ttu-id="d5f71-146">如何：安裝和設定 WCF 啟用元件</span><span class="sxs-lookup"><span data-stu-id="d5f71-146">How to: Install and Configure WCF Activation Components</span></span>](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [<span data-ttu-id="d5f71-147">Windows Server App Fabric 主控功能</span><span class="sxs-lookup"><span data-stu-id="d5f71-147">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)

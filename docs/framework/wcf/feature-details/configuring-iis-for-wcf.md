---
title: 設定 Internet Information Services 7.0 for Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 369fd641adc91c58a676a7c2708e267366d73b41
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838048"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a><span data-ttu-id="f76f0-102">設定 Internet Information Services 7.0 for Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f76f0-102">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>

<span data-ttu-id="f76f0-103">Internet Information Services (IIS) 7.0 具有模組化的設計，可以讓您選擇性地安裝所需的元件。</span><span class="sxs-lookup"><span data-stu-id="f76f0-103">Internet Information Services (IIS) 7.0 has a modular design that allows you to selectively install components that are required.</span></span> <span data-ttu-id="f76f0-104">這項設計是以 Windows Vista 引進的新資訊清單驅動元件化技術為基礎。</span><span class="sxs-lookup"><span data-stu-id="f76f0-104">This design is based on the new manifest-driven componentization technology introduced in Windows Vista.</span></span> <span data-ttu-id="f76f0-105">IIS 7.0 有超過40個獨立功能元件可獨立安裝。</span><span class="sxs-lookup"><span data-stu-id="f76f0-105">There are more than 40 standalone feature components of IIS 7.0 that can be installed independently.</span></span> <span data-ttu-id="f76f0-106">這讓 IT 專業人員能夠輕鬆地依其需要自訂安裝。</span><span class="sxs-lookup"><span data-stu-id="f76f0-106">This allows IT professionals to easily customize the installation as required.</span></span> <span data-ttu-id="f76f0-107">本主題討論如何設定 IIS 7.0 搭配 Windows Communication Foundation （WCF）使用，並判斷需要哪些元件。</span><span class="sxs-lookup"><span data-stu-id="f76f0-107">This topic discusses how to configure IIS 7.0 for use with Windows Communication Foundation (WCF) and determine which components are required.</span></span>

## <a name="minimal-installation-installing-was"></a><span data-ttu-id="f76f0-108">基本安裝：安裝 WAS</span><span class="sxs-lookup"><span data-stu-id="f76f0-108">Minimal Installation: Installing WAS</span></span>
 <span data-ttu-id="f76f0-109">整個 IIS 7.0 套件的最小安裝是安裝 Windows 進程啟用服務（WAS）。</span><span class="sxs-lookup"><span data-stu-id="f76f0-109">The minimal installation of the whole IIS 7.0 package is to install the Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="f76f0-110">WAS 是獨立的功能，而且是 IIS 7.0 中的唯一功能，適用于所有 Windows Vista 作業系統（Home Basic、Home Premium、Business、旗艦版和企業版）。</span><span class="sxs-lookup"><span data-stu-id="f76f0-110">WAS is a standalone feature and it is the only feature from the IIS 7.0 that is available for all Windows Vista operating systems (Home Basic, Home Premium, Business, and Ultimate and Enterprise).</span></span>

 <span data-ttu-id="f76f0-111">從 [控制台] 按一下 [**程式**]，然後按一下 [**程式和功能**] 底下的 [**開啟或關閉 WINDOWS 功能**]，[WAS] 元件會顯示在清單中，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="f76f0-111">From the Control Panel, click **Programs** and then click **Turn Windows features on or off** which is listed under **Programs and Features**, the WAS component is shown in the list as in the following illustration.</span></span>

 <span data-ttu-id="f76f0-112">![開啟或關閉功能對話方塊](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span><span class="sxs-lookup"><span data-stu-id="f76f0-112">![Turn Features On or Off Dialog](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span></span>

 <span data-ttu-id="f76f0-113">這項功能具有下列子元件：</span><span class="sxs-lookup"><span data-stu-id="f76f0-113">This feature has the following sub-components:</span></span>

- <span data-ttu-id="f76f0-114">.NET 環境</span><span class="sxs-lookup"><span data-stu-id="f76f0-114">.NET Environment</span></span>

- <span data-ttu-id="f76f0-115">組態 API</span><span class="sxs-lookup"><span data-stu-id="f76f0-115">Configuration APIs</span></span>

- <span data-ttu-id="f76f0-116">處理序模型</span><span class="sxs-lookup"><span data-stu-id="f76f0-116">Process Model</span></span>

 <span data-ttu-id="f76f0-117">如果您選取 WAS 的根節點，預設只會核取 [**進程模型**] 子節點。</span><span class="sxs-lookup"><span data-stu-id="f76f0-117">If you select the root node of WAS, only the **Process Model** sub-node is checked by default.</span></span> <span data-ttu-id="f76f0-118">請注意，進行這項安裝時只會安裝 WAS，因為此時不支援 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="f76f0-118">Please note that with this installation you are only installing WAS, because there is no support for a Web server.</span></span>

 <span data-ttu-id="f76f0-119">若要讓 WCF 或任何 ASP.NET 應用程式正常執行，請核取 [ **.Net 環境**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f76f0-119">To make WCF or any ASP.NET application work, check the **.NET Environment** checkbox.</span></span> <span data-ttu-id="f76f0-120">這表示，所有 WAS 元件都必須讓 WCF 和 ASP.NET 運作良好。</span><span class="sxs-lookup"><span data-stu-id="f76f0-120">This means that all of WAS components are required to make WCF and ASP.NET to work well.</span></span> <span data-ttu-id="f76f0-121">一旦您安裝任何其中一個上述元件，這些應用程式便會自動核取。</span><span class="sxs-lookup"><span data-stu-id="f76f0-121">These are automatically checked once you install any of those components.</span></span>

## <a name="iis-70-default-installation"></a><span data-ttu-id="f76f0-122">IIS 7.0：預設安裝</span><span class="sxs-lookup"><span data-stu-id="f76f0-122">IIS 7.0: Default Installation</span></span>
 <span data-ttu-id="f76f0-123">藉由檢查**Internet Information Services**功能，會自動檢查部分子節點，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="f76f0-123">By checking the **Internet Information Services** feature, some of the sub-nodes are automatically checked as shown in the following illustration.</span></span>

 <span data-ttu-id="f76f0-124">![IIS 7.0 功能的預設設定](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span><span class="sxs-lookup"><span data-stu-id="f76f0-124">![Default settings for IIS 7.0 features](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span></span>

 <span data-ttu-id="f76f0-125">這是 IIS 7.0 的預設安裝。</span><span class="sxs-lookup"><span data-stu-id="f76f0-125">This is the default installation of IIS 7.0.</span></span> <span data-ttu-id="f76f0-126">在此安裝中，您可以使用 IIS 7.0 來服務靜態內容（例如 HTML 頁面和其他內容）。</span><span class="sxs-lookup"><span data-stu-id="f76f0-126">With this installation, you can use IIS 7.0 to service static content (such as HTML pages and other content).</span></span> <span data-ttu-id="f76f0-127">不過，您無法執行 ASP.NET 或 CGI 應用程式或裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="f76f0-127">However, you cannot run ASP.NET or CGI applications or host WCF services.</span></span>

## <a name="iis-70-installation-with-aspnet-support"></a><span data-ttu-id="f76f0-128">IIS 7.0：具有 ASP.NET 支援的安裝</span><span class="sxs-lookup"><span data-stu-id="f76f0-128">IIS 7.0: Installation with ASP.NET Support</span></span>
 <span data-ttu-id="f76f0-129">您必須安裝 ASP.NET，才能在 IIS 7.0 上進行 ASP.NET 工作。</span><span class="sxs-lookup"><span data-stu-id="f76f0-129">You must install ASP.NET to make ASP.NET work on IIS 7.0.</span></span> <span data-ttu-id="f76f0-130">檢查**ASP.NET**之後，您的畫面看起來應該如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="f76f0-130">After checking **ASP.NET**, your screen should look like the following illustration.</span></span>

 <span data-ttu-id="f76f0-131">![Asp.NET 必要設定](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span><span class="sxs-lookup"><span data-stu-id="f76f0-131">![Asp.NET required settings](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span></span>

 <span data-ttu-id="f76f0-132">這是 WCF 和 ASP.NET 應用程式在 IIS 7.0 中工作的最小環境。</span><span class="sxs-lookup"><span data-stu-id="f76f0-132">This is the minimal environment for both WCF and ASP.NET applications to work in IIS 7.0.</span></span>

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a><span data-ttu-id="f76f0-133">IIS 7.0：具有 IIS 6.0 相容性元件的安裝</span><span class="sxs-lookup"><span data-stu-id="f76f0-133">IIS 7.0: Installation with IIS 6.0 Compatibility Components</span></span>
 <span data-ttu-id="f76f0-134">在具有 Visual Studio 2005 的系統或一些其他自動化腳本或工具（例如 Adsutil.vbs）上安裝 IIS 7.0 時，若設定的虛擬應用程式使用 IIS 6.0 元資料庫 API，請務必檢查 IIS 6.0**腳本工具**。</span><span class="sxs-lookup"><span data-stu-id="f76f0-134">When installing IIS 7.0 on a system with Visual Studio 2005 or some other automation scripts or tools (such as Adsutil.vbs) that configure virtual applications that use IIS 6.0 Metabase API, ensure that you check the IIS 6.0 **Scripting Tools**.</span></span> <span data-ttu-id="f76f0-135">這會自動檢查 IIS 6.0**管理相容性**的其他子節點。</span><span class="sxs-lookup"><span data-stu-id="f76f0-135">This automatically checks the other sub-nodes of IIS 6.0 **Management Compatibility**.</span></span> <span data-ttu-id="f76f0-136">下圖顯示完成後的畫面：</span><span class="sxs-lookup"><span data-stu-id="f76f0-136">The following illustration shows the screen after this is done:</span></span>

 <span data-ttu-id="f76f0-137">![IIS 6.0 管理相容性設定](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span><span class="sxs-lookup"><span data-stu-id="f76f0-137">![IIS 6.0 Management Compatibility Settings](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span></span>

 <span data-ttu-id="f76f0-138">在此安裝中，您會有使用 IIS 7.0、ASP.NET 和 WCF 功能所需的所有專案，以及可在網站上取得的範例。</span><span class="sxs-lookup"><span data-stu-id="f76f0-138">With this installation, you have everything required to use IIS 7.0, ASP.NET and WCF features and samples available on the Web.</span></span>

## <a name="request-limits"></a><span data-ttu-id="f76f0-139">要求限制</span><span class="sxs-lookup"><span data-stu-id="f76f0-139">Request Limits</span></span>
 <span data-ttu-id="f76f0-140">在 Windows Vista （含 IIS 7）上，`maxUri` 和 `maxQueryStringSize` 設定的預設值已變更。</span><span class="sxs-lookup"><span data-stu-id="f76f0-140">On Windows Vista with IIS 7 the default value of the `maxUri` and `maxQueryStringSize` settings have been changed.</span></span> <span data-ttu-id="f76f0-141">根據預設，IIS 7.0 中的要求篩選允許 URL 長度為 4096 個字元，查詢字串長度為 2048 個字元。</span><span class="sxs-lookup"><span data-stu-id="f76f0-141">By default, request filtering in IIS 7.0 allows a URL length of 4096 characters and a query string length of 2048 characters.</span></span> <span data-ttu-id="f76f0-142">若要變更這些預設值，請將下列 XML 加入至您的 App.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="f76f0-142">To change these defaults add the following XML to your App.config file.</span></span>

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a><span data-ttu-id="f76f0-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="f76f0-143">See also</span></span>

- [<span data-ttu-id="f76f0-144">WAS 啟用架構</span><span class="sxs-lookup"><span data-stu-id="f76f0-144">WAS Activation Architecture</span></span>](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [<span data-ttu-id="f76f0-145">設定用於 WCF 的 WAS</span><span class="sxs-lookup"><span data-stu-id="f76f0-145">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [<span data-ttu-id="f76f0-146">如何：安裝和設定 WCF 啟用元件</span><span class="sxs-lookup"><span data-stu-id="f76f0-146">How to: Install and Configure WCF Activation Components</span></span>](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [<span data-ttu-id="f76f0-147">Windows Server AppFabric 裝載功能</span><span class="sxs-lookup"><span data-stu-id="f76f0-147">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)

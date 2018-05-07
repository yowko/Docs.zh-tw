---
title: 設定 Internet Information Services 7.0 for Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 3e34f46fbf3ccf12c6a89a7cac96143965d958d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>設定 Internet Information Services 7.0 for Windows Communication Foundation
Internet Information Services (IIS) 7.0 具有模組化的設計，可以讓您選擇性地安裝所需的元件。 這項設計是以 [!INCLUDE[wv](../../../../includes/wv-md.md)]中引進的新資訊清單驅動元件化技術為基礎。 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 有超過 40 項可以個別安裝的獨立功能元件。 這讓 IT 專業人員能夠輕鬆地依其需要自訂安裝。 本主題討論如何設定[!INCLUDE[iisver](../../../../includes/iisver-md.md)]的使用與 Windows Communication Foundation (WCF)，並判斷所需的元件。  
  
## <a name="minimal-installation-installing-was"></a>基本安裝：安裝 WAS  
 完整 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 套件的基本安裝是安裝 Windows Process Activation Service (WAS)。 WAS 是獨立的功能，而且是唯一能在所有 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 作業系統 (Home Basic、Home Premium、Business、Ultimate 及 Enterprise) 上提供的 [!INCLUDE[wv](../../../../includes/wv-md.md)] 功能。  
  
 從 [控制台] 中按一下**程式**，然後按一下 [**開啟或關閉 Windows 功能**] 下**程式和功能**，WAS 元件隨即顯示清單中，如下圖所示。  
  
 ![功能開啟或關閉對話方塊](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")  
  
 這項功能具有下列子元件：  
  
-   .NET 環境  
  
-   組態 API  
  
-   處理序模型  
  
 如果您選取 WAS 的根節點僅**處理序模型**預設會核取子節點。 請注意，進行這項安裝時只會安裝 WAS，因為此時不支援 Web 伺服器。  
  
 若要讓 WCF 或任何[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]應用程式運作，請檢查 **.NET 環境**核取方塊。 這表示所有的 WAS 元件都需要讓 WCF 和[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]無法正常運作。 一旦您安裝任何其中一個上述元件，這些應用程式便會自動核取。  
  
## <a name="iis-70-default-installation"></a>IIS 7.0：預設安裝  
 藉由檢查**Internet Information Services**功能，某些子節點會自動核取下圖所示。  
  
 ![IIS 7.0 功能的預設設定](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")  
  
 這是 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 的預設安裝。 運用這項安裝，您可以使用 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 來提供靜態內容的服務 (例如 HTML 頁面和其他內容)。 不過，您無法執行[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]或 CGI 應用程式或裝載 WCF 服務。  
  
## <a name="iis-70-installation-with-aspnet-support"></a>IIS 7.0：具有 ASP.NET 支援的安裝  
 您必須安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 才能讓 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 在 IIS 7.0 上運作。 檢查後**ASP.NET**，您的畫面應該看起來像下圖。  
  
 ![Asp.NET 必要設定](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")  
  
 這是這兩個 WCF 環境的最小和[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]應用程式運作[!INCLUDE[iisver](../../../../includes/iisver-md.md)]。  
  
## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>IIS 7.0：具有 IIS 6.0 相容性元件的安裝  
 安裝時[!INCLUDE[iisver](../../../../includes/iisver-md.md)]Visual Studio 2005 或某些其他自動化指令碼或工具 （例如 Adsutil.vbs) 設定使用的虛擬應用程式的系統上[!INCLUDE[iis601](../../../../includes/iis601-md.md)]Metabase API，請確定[!INCLUDE[iis601](../../../../includes/iis601-md.md)] **指令碼工具**。 這會自動檢查的其他子節點[!INCLUDE[iis601](../../../../includes/iis601-md.md)]**管理相容性**。 下圖顯示完成此步驟之後的畫面。  
  
 ![IIS 6.0 管理相容性設定](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")  
  
 透過這項安裝，您可以使用所需的所有[!INCLUDE[iisver](../../../../includes/iisver-md.md)]， [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 上提供範例和 WCF 的功能。  
  
## <a name="request-limits"></a>要求限制  
 在具有 IIS 7 的 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上，`maxUri` 和 `maxQueryStringSize` 設定的預設值已經變更。 根據預設，IIS 7.0 中的要求篩選允許 URL 長度為 4096 個字元，查詢字串長度為 2048 個字元。 若要變更這些預設值，請將下列 XML 加入至您的 App.config 檔中。  
  
 `<system.webServer>`  
  
 `<security>`  
  
 `<requestFiltering>`  
  
 `<requestLimits maxUrl="8192" maxQueryString="8192" />`  
  
 `</requestFiltering>`  
  
 `</security>`  
  
 `</system.webServer>`  
  
## <a name="see-also"></a>另請參閱  
 [WAS 啟用架構](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)  
 [設定用於 WCF 的 WAS](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [如何：安裝和設定 WCF 啟用元件](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
 [Windows Server App Fabric 裝載功能](http://go.microsoft.com/fwlink/?LinkId=201276)

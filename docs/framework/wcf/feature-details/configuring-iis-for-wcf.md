---
title: 設定 Internet Information Services 7.0 for Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 53ba48d47d30bd94ae5544920041cd430526223b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710286"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>設定 Internet Information Services 7.0 for Windows Communication Foundation

Internet Information Services (IIS) 7.0 具有模組化的設計，可以讓您選擇性地安裝所需的元件。 這項設計是以 [!INCLUDE[wv](../../../../includes/wv-md.md)]中引進的新資訊清單驅動元件化技術為基礎。 有 40 個以上的獨立功能元件，可獨立安裝的 IIS 7.0。 這讓 IT 專業人員能夠輕鬆地依其需要自訂安裝。 本主題討論如何設定 IIS 7.0 使用與 Windows Communication Foundation (WCF)，並判斷需要哪些元件。

## <a name="minimal-installation-installing-was"></a>最小安裝：安裝 WAS
 整個 IIS 7.0 封裝的基本安裝是安裝 Windows Process Activation Service (WAS)。 已是獨立功能，它是唯一的功能，可供所有 IIS 7.0[!INCLUDE[wv](../../../../includes/wv-md.md)]作業系統 （Home Basic、 Home Premium、 Business 和 Ultimate 和 Enterprise）。

 從 控制台 中按一下**程式**，然後按一下**開啟 Windows 功能開啟或關閉** 下**程式和功能**，WAS 元件所示如下列圖所示的清單。

 ![功能開啟或關閉對話方塊](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")

 這項功能具有下列子元件：

-   .NET 環境

-   組態 API

-   處理序模型

 如果您選取根節點的 WAS，只有**處理序模型**子節點依預設會勾選。 請注意，進行這項安裝時只會安裝 WAS，因為此時不支援 Web 伺服器。

 若要讓 WCF 或任何 ASP.NET 應用程式工作，請檢查 **.NET 環境**核取方塊。 這表示所有的 WAS 元件都需要進行 WCF 和 ASP.NET 無法正常運作。 一旦您安裝任何其中一個上述元件，這些應用程式便會自動核取。

## <a name="iis-70-default-installation"></a>IIS 7.0:預設安裝
 藉由檢查**Internet Information Services**如下圖所示，會自動檢查功能，某些子節點。

 ![IIS 7.0 功能的預設值](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")

 這是 IIS 7.0 的預設安裝。 這項安裝，您可以使用 IIS 7.0 來服務靜態內容 （例如 HTML 網頁和其他內容）。 不過，您無法執行 ASP.NET 或 CGI 應用程式或裝載 WCF 服務。

## <a name="iis-70-installation-with-aspnet-support"></a>IIS 7.0:安裝具有 ASP.NET 支援
 您必須安裝 ASP.NET，讓 ASP.NET 在 IIS 7.0 上運作。 檢查後**ASP.NET**，您的畫面應該看起來類似下圖。

 ![Asp.NET 必要設定](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")

 這是最小的環境，讓 IIS 7.0 中運作的 WCF 和 ASP.NET 應用程式。

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>IIS 7.0:與 IIS 6.0 的相容性元件的安裝
 當 Visual Studio 2005 或其他自動化指令碼或設定使用 IIS 6.0 Metabase API 的虛擬應用程式的工具 （例如 Adsutil.vbs) 的系統上安裝 IIS 7.0，請確定您檢查 IIS 6.0**指令碼工具**. 這會自動檢查 IIS 6.0 的其他子節點**管理相容性**。 這麼做之後下, 圖顯示的畫面：

 ![IIS 6.0 管理相容性設定](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")

 此安裝中，您可以使用網頁上的 IIS 7.0、 ASP.NET 和 WCF 的功能和可用的範例所需的所有項目。

## <a name="request-limits"></a>要求限制
 在具有 IIS 7 的 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上，`maxUri` 和 `maxQueryStringSize` 設定的預設值已經變更。 根據預設，IIS 7.0 中的要求篩選允許 URL 長度為 4096 個字元，查詢字串長度為 2048 個字元。 若要變更這些預設值，請將下列 XML 加入至您的 App.config 檔中。

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a>另請參閱

- [WAS 啟用架構](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [設定用於 WCF 的 WAS](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [如何：安裝及設定 WCF 啟用元件](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [Windows Server AppFabric 裝載功能](https://go.microsoft.com/fwlink/?LinkId=201276)

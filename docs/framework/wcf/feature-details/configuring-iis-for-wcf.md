---
title: 設定 Internet Information Services 7.0 for Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 41eedcf78d8ca6f10fcd0380e43420dcc1b328f1
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964511"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>設定 Internet Information Services 7.0 for Windows Communication Foundation

Internet Information Services (IIS) 7.0 具有模組化的設計，可以讓您選擇性地安裝所需的元件。 這項設計是以 Windows Vista 引進的新資訊清單驅動元件化技術為基礎。 IIS 7.0 有超過40個獨立功能元件可獨立安裝。 這讓 IT 專業人員能夠輕鬆地依其需要自訂安裝。 本主題討論如何設定 IIS 7.0 搭配 Windows Communication Foundation （WCF）使用，並判斷需要哪些元件。

## <a name="minimal-installation-installing-was"></a>基本安裝：安裝 WAS
 整個 IIS 7.0 套件的最小安裝是安裝 Windows 進程啟用服務（WAS）。 WAS 是獨立的功能，而且是 IIS 7.0 中的唯一功能，適用于所有 Windows Vista 作業系統（Home Basic、Home Premium、Business、旗艦版和企業版）。

 從 [控制台] 按一下 [**程式**]，然後按一下 [**程式和功能**] 底下的 [**開啟或關閉 WINDOWS 功能**]，[WAS] 元件會顯示在清單中，如下圖所示。

 ![開啟或關閉功能對話方塊](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")

 這項功能具有下列子元件：

- .NET 環境

- 組態 API

- 處理序模型

 如果您選取 WAS 的根節點，預設只會核取 [**進程模型**] 子節點。 請注意，進行這項安裝時只會安裝 WAS，因為此時不支援 Web 伺服器。

 若要讓 WCF 或任何 ASP.NET 應用程式正常執行，請核取 [ **.Net 環境**] 核取方塊。 這表示，所有 WAS 元件都必須讓 WCF 和 ASP.NET 運作良好。 一旦您安裝任何其中一個上述元件，這些應用程式便會自動核取。

## <a name="iis-70-default-installation"></a>IIS 7.0：預設安裝
 藉由檢查**Internet Information Services**功能，會自動檢查部分子節點，如下圖所示。

 ![IIS 7.0 功能的預設設定](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")

 這是 IIS 7.0 的預設安裝。 在此安裝中，您可以使用 IIS 7.0 來服務靜態內容（例如 HTML 頁面和其他內容）。 不過，您無法執行 ASP.NET 或 CGI 應用程式或裝載 WCF 服務。

## <a name="iis-70-installation-with-aspnet-support"></a>IIS 7.0：具有 ASP.NET 支援的安裝
 您必須安裝 ASP.NET，才能在 IIS 7.0 上進行 ASP.NET 工作。 檢查**ASP.NET**之後，您的畫面看起來應該如下圖所示。

 ![Asp.NET 必要設定](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")

 這是 WCF 和 ASP.NET 應用程式在 IIS 7.0 中工作的最小環境。

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>IIS 7.0：具有 IIS 6.0 相容性元件的安裝
 在具有 Visual Studio 2005 的系統或一些其他自動化腳本或工具（例如 Adsutil.vbs）上安裝 IIS 7.0 時，若設定的虛擬應用程式使用 IIS 6.0 元資料庫 API，請務必檢查 IIS 6.0**腳本工具**。 這會自動檢查 IIS 6.0**管理相容性**的其他子節點。 下圖顯示完成後的畫面：

 ![IIS 6.0 管理相容性設定](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")

 在此安裝中，您會有使用 IIS 7.0、ASP.NET 和 WCF 功能所需的所有專案，以及可在網站上取得的範例。

## <a name="request-limits"></a>要求限制
 在 Windows Vista （含 IIS 7）上，`maxUri` 和 `maxQueryStringSize` 設定的預設值已變更。 根據預設，IIS 7.0 中的要求篩選允許 URL 長度為 4096 個字元，查詢字串長度為 2048 個字元。 若要變更這些預設值，請將下列 XML 加入至您的 App.config 檔中。

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a>請參閱

- [WAS 啟用架構](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [設定用於 WCF 的 WAS](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [如何：安裝和設定 WCF 啟用元件](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [Windows Server AppFabric 裝載功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))

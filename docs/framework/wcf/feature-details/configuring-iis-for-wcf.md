---
title: "設定 Internet Information Services 7.0 for Windows Communication Foundation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 設定 Internet Information Services 7.0 for Windows Communication Foundation
Internet Information Services \(IIS\) 7.0 具有模組化的設計，可以讓您選擇性地安裝所需的元件。這項設計是以 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中引進的新資訊清單驅動元件化技術為基礎。[!INCLUDE[iisver](../../../../includes/iisver-md.md)] 有超過 40 項可以個別安裝的獨立功能元件。這讓 IT 專業人員能夠輕鬆地依其需要自訂安裝。本主題會討論如何設定 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 以搭配 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 使用，並判斷需要哪些元件。  
  
## 基本安裝：安裝 WAS  
 完整 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 套件的基本安裝是安裝 Windows Process Activation Service \(WAS\)。WAS 是獨立的功能，而且是唯一能在所有 [!INCLUDE[wv](../../../../includes/wv-md.md)] 作業系統 \(Home Basic、Home Premium、Business、Ultimate 及 Enterprise\) 上提供的 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 功能。  
  
 從 \[控制台\] 按一下 \[**程式**\]，然後按一下 \[**程式和功能**\] 下的 \[**開啟或關閉 Windows 功能**\]，WAS 元件隨即顯示在清單中，如下圖所示。  
  
 ![開啟或關閉功能對話方塊](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc\_TurnFeaturesOnOrOffs")  
  
 這項功能具有下列子元件：  
  
-   .NET 環境  
  
-   組態 API  
  
-   處理序模型  
  
 如果是選取 WAS 的根節點，根據預設將只核取 \[**處理序模型**\] 子節點。請注意，進行這項安裝時只會安裝 WAS，因為此時不支援 Web 伺服器。  
  
 若要讓 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 或任何 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式運作，請核取 \[**.NET 環境**\] 核取方塊。這表示需要所有的 WAS 元件才能讓 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 與 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 正常運作。一旦您安裝任何其中一個上述元件，這些應用程式便會自動核取。  
  
## IIS 7.0：預設安裝  
 透過核取 \[**網際網路資訊服務**\] 功能，便會自動核取一些子節點，如下圖所示。  
  
 ![IIS 7.0 功能的預設設定](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc\_TurningFeaturesOnOrOff2")  
  
 這是 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 的預設安裝。運用這項安裝，您可以使用 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 來提供靜態內容的服務 \(例如 HTML 頁面和其他內容\)。不過，您無法執行 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 或 CGI 應用程式，或是裝載 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。  
  
## IIS 7.0：具有 ASP.NET 支援的安裝  
 您必須安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 才能讓 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 在 IIS 7.0 上運作。在核取 \[**ASP.NET**\] 之後，您的畫面應該看起來類似下圖。  
  
 ![ASP.NET 的必要設定](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc\_TrunFeaturesOnOrOFf3s")  
  
 這是讓 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 與 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式在 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 中運作的基本環境。  
  
## IIS 7.0：具有 IIS 6.0 相容性元件的安裝  
 若是在系統上，使用會將虛擬應用程式設定成使用 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] Metabase API 之 Visual Studio 2005 或其他一些自動化指令碼或工具 \(例如 Adsutil.vbs\) 來安裝 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 時，請確定核取 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 的 \[**指令碼工具**\]。這樣便會自動核取 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] \[**管理相容性**\] 的其他子節點。下圖顯示完成此步驟之後的畫面。  
  
 ![IIS 6.0 管理相容性設定](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc\_TurnFeaturesOnOrOff5s")  
  
 運用這項安裝，您便具備使用 [!INCLUDE[iisver](../../../../includes/iisver-md.md)]、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 功能以及 Web 上提供範例的必要條件。  
  
## 要求限制  
 在具有 IIS 7 的 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上，`maxUri` 和 `maxQueryStringSize` 設定的預設值已經變更。根據預設，IIS 7.0 中的要求篩選允許 URL 長度為 4096 個字元，查詢字串長度為 2048 個字元。若要變更這些預設值，請將下列 XML 加入至您的 App.config 檔中。  
  
 `<system.webServer>`  
  
 `<security>`  
  
 `<requestFiltering>`  
  
 `<requestLimits maxUrl=”8192” maxQueryString=”8192” />`  
  
 `</requestFiltering>`  
  
 `</security>`  
  
 `</system.webServer>`  
  
## 請參閱  
 [WAS 啟用架構](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)   
 [設定用於 WCF 的 WAS](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)   
 [HOW TO：安裝和設定 WCF 啟用元件](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)   
 [Windows Server AppFabric 主控功能](http://go.microsoft.com/fwlink/?LinkId=201276)
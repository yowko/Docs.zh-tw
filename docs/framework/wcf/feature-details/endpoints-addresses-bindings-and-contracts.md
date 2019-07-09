---
title: 端點：位址、繫結和合約
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 361ed623e50b409147387a0edec7f42c733f3d48
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664129"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a>端點：位址、繫結和合約

使用 Windows Communication Foundation (WCF) 服務的所有通訊都都會透過*端點*的服務。 端點可讓用戶端存取至 WCF 服務所提供的功能。

端點包含四項屬性：

- 指出可在何處找到端點的位址。

- 指定用戶端可以如何與端點通訊的繫結。

- 識別可用作業的合約。

- 指定本機端點實作細節的行為集。

本主題會討論這個端點結構，並說明它的 WCF 物件模型中的呈現方式。

## <a name="the-structure-of-an-endpoint"></a>端點結構

每個端點都包含下列項目：

- 位址:位址可唯一識別端點並告訴潛在取用者服務，其位於何處。 它由 WCF 物件模型中代表<xref:System.ServiceModel.EndpointAddress>類別。 <xref:System.ServiceModel.EndpointAddress> 類別包含：

  - <xref:System.ServiceModel.EndpointAddress.Uri%2A> 屬性，用來代表服務位址。

  - <xref:System.ServiceModel.EndpointAddress.Identity%2A> 屬性，用來代表服務的安全性身分識別以及一群選用的訊息標頭集合。 選用訊息標頭會用來提供其他更詳細的定址資訊來識別端點或與端點互動。

  如需詳細資訊，請參閱 <<c0> [ 指定端點位址](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)。

- 繫結：繫結會指定與端點的通訊方式。 包括：

  - 要使用的傳輸通訊協定 (例如，TCP 或 HTTP)。

  - 訊息使用的編碼 (例如，文字或二進位)。

  - 必要的安全性需求 (例如，SSL 或 SOAP 訊息安全性)。

  如需詳細資訊，請參閱 < [WCF 繫結概觀](../../../../docs/framework/wcf/bindings-overview.md)。 繫結由 WCF 物件模型中的抽象基底類別<xref:System.ServiceModel.Channels.Binding>。 在大部分情況中，使用者可以使用下列其中一種系統提供的繫結。 如需詳細資訊，請參閱 < [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md)。

- 合約：合約會概略說明端點公開給用戶端哪些功能。 合約會指定：

  - 用戶端可以呼叫的作業。

  - 訊息格式。

  - 呼叫作業所需的輸入參數或資料型別。

  - 用戶端可以期待收到的處理或回應訊息型別。

  如需有關如何定義合約的詳細資訊，請參閱 < [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md)。

- 行為：您可以使用端點行為來自訂服務端點的本機行為。 端點行為會藉由參與建置 WCF 執行階段的過程中達到此目的。 <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> 屬性是一個端點行為範例，它可讓您指定不同於 SOAP 或 Web 服務描述語言 (WSDL) 位址的接聽位址。 如需詳細資訊，請參閱 < [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md)。

## <a name="defining-endpoints"></a>定義端點

您可以透過命令式程式碼或是宣告式組態來指定服務端點。 如需詳細資訊，請參閱[如何：在組態中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)和[How to:在程式碼中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)。

## <a name="in-this-section"></a>本節內容

本章節說明繫結、端點與位址的用途；說明如何設定繫結與端點；並示範如何使用 `ClientVia` 行為和 `ListenUri` 屬性。

[地址](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)\
描述如何在 WCF 中處理端點。

[繫結](../../../../docs/framework/wcf/feature-details/bindings.md)\
說明如何使用繫結程序來指定必要的傳輸、編碼與通訊協定詳細資料，以供用戶端與服務彼此通訊。

[合約](../../../../docs/framework/wcf/feature-details/contracts.md)\
說明合約如何定義服務方法。

[如何：在組態中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)\
說明如何透過組態建立服務端點。

[如何：在程式碼中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)\
說明如何透過程式碼建立服務端點。

[如何：使用 Svcutil.exe 來驗證已編譯的服務程式碼](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)\
描述如何在服務實作和設定中偵測到錯誤，而不需要裝載服務會使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。

## <a name="see-also"></a>另請參閱

- [設定服務](../../../../docs/framework/wcf/configuring-services.md)
- [擴充繫結](../../../../docs/framework/wcf/extending/extending-bindings.md)

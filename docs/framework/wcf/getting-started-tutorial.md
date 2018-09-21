---
title: 開始使用 Tutorial1
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], getting started
- Windows Communication Foundation [WCF], getting started
- getting started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 204869d0a7a7b8d56449c28cb37b18624a1701cf
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46539651"
---
# <a name="getting-started-tutorial"></a>快速入門教學課程

在本節中所包含的主題旨在讓您快速獲得至 Windows Communication Foundation (WCF) 程式設計經驗。 每個主題已設計成依本主題結尾的清單順序完成。 循序完成本教學課程可讓您建立 WCF 服務和用戶端應用程式所需的步驟大致了解。 服務會公開一個或多個端點，而其中每個端點都會公開一項或多項服務作業。 *端點*服務的指定位置可以找到服務，包含的資訊，說明服務與合約定義的功能，用戶端必須之間的通訊的繫結位址服務提供給其用戶端。

 在您逐步執行本教學課程中各主題的程序之後，您將會有執行中的服務和呼叫服務的用戶端。 前面三個主題說明如何定義服務合約、如何實作服務合約以及如何裝載服務。 建立的這個服務是在主控台應用程式中自我裝載的服務。 服務也可以在網際網路資訊服務 (IIS) 之下進行裝載。 如需如何執行這項操作的詳細資訊，請參閱[如何： 將 WCF 服務裝載於 IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。 服務是在程式碼中進行設定的，但是也可以在組態檔中設定。 如需使用組態檔的詳細資訊，請參閱[設定服務使用組態檔](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)。

 後面三個主題將說明如何建立用戶端 Proxy、設定用戶端應用程式，以及使用用戶端 Proxy 來呼叫服務所公開的服務作業。 服務會發行定義用戶端應用程式與服務進行通訊所需之資訊的中繼資料。 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 會自動化存取這個中繼資料的程序，並用它來建構和設定服務的用戶端應用程式。 如果您不使用[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]，您可以使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來建構和設定服務的用戶端應用程式。

在本節中的主題會假設您使用 Visual Studio 作為開發環境。 如果您使用另一個開發環境，請略過 Visual Studio 特定指示。

範例應用程式，可以下載到您的硬碟並執行，請參閱中的主題[Windows Communication Foundation 範例](https://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)。 本主題中，特別是，請參閱[開始使用](../../../docs/framework/wcf/samples/getting-started-sample.md)。

如需建立服務和用戶端的詳細深入資訊，請參閱 <<c0> [ 基本 WCF 程式設計](../../../docs/framework/wcf/basic-wcf-programming.md)。

## <a name="in-this-section"></a>本節內容
 [如何：定義服務合約](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)

 描述如何建立 WCF 合約使用使用者定義的介面。 合約會定義服務所公開的功能。

 [如何：履行服務合約](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)

 說明如何實作服務合約。 一旦定義了合約，就必須透過服務類別加以實作。

 [如何：裝載及執行基本服務](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)

 說明如何在程式碼中設定服務的端點，以及如何在主控台應用程式中裝載服務。 如果要成為作用中的服務，必須在執行階段環境中設定與裝載服務。 此環境會建立服務並控制其內容與存留期。

 [如何：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)

 描述如何擷取用來從 WCF 服務建立 WCF 用戶端 proxy 的中繼資料。 此程序會使用 Visual Studio 中的新增服務參考 功能。

 [如何：設定用戶端](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)

 說明如何設定 WCF 用戶端。設定用戶端時，需要指定用戶端用來存取服務的端點。

 [如何：使用用戶端](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)

 描述如何使用 WCF 用戶端 proxy 叫用服務作業。

## <a name="reference"></a>參考資料

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="related-sections"></a>相關章節

- [Windows Communication Foundation 範例](https://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)
- [基本程式設計週期](../../../docs/framework/wcf/basic-programming-lifecycle.md)

## <a name="see-also"></a>另請參閱

- [概念性概觀](../../../docs/framework/wcf/conceptual-overview.md)
- [文件指南](../../../docs/framework/wcf/guide-to-the-documentation.md)
- [什麼是 Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)
- [WCF 功能詳細資料](../../../docs/framework/wcf/feature-details/index.md)
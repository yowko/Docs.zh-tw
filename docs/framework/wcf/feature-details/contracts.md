---
title: 合約
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], contracts
- contracts [WCF]
- Windows Communication Foundation [WCF], contracts
ms.assetid: c8364183-4ac1-480b-804a-c5e6c59a5d7d
ms.openlocfilehash: 0443e5b37e637351d6491c37ec443c93636460a3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134884"
---
# <a name="contracts"></a>合約
本節將說明如何定義及實作 Windows Communication Foundation (WCF) 合約。 服務合約會指定端點與外界溝通的內容。 更具體來說，這是關於一組會組織到基本訊息交換模式 (MEP) 之特定訊息的聲明，而這些交換模式包括要求/回覆、單向和雙工。 如果服務合約為一組邏輯相關的訊息交換，則服務作業就是單一的訊息交換。 例如，`Hello` 作業一定會明確地接收一個訊息 (這樣呼叫端才能宣告歡迎畫面)，但卻不一定會傳回訊息 (需視作業的禮節而定)。  
  
 如需合約以及其他核心 WCF 概念的詳細資訊，請參閱[基本 Windows Communication Foundation 的概念](../../../../docs/framework/wcf/fundamental-concepts.md)。 本主題將著重於讓您了解服務合約。 如需如何建置使用服務合約連線到服務的用戶端的詳細資訊，請參閱[WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md)。 如需用戶端通道、 用戶端架構以及其他用戶端問題的詳細資訊，請參閱[用戶端](../../../../docs/framework/wcf/feature-details/clients.md)。  
  
## <a name="overview"></a>總覽  
 本主題提供設計與實作 WCF 服務的高層級概念方向。 副標題則提供設計和實作之細節的詳細資訊。 設計和實作之前 WCF 應用程式，建議您：  
  
-   瞭解服務合約是什麼、如何使用它，以及如何建立它。  
  
-   瞭解合約會聲明執行階段組態或裝載環境不一定會支援的最低需求。  
  
## <a name="service-contracts"></a>服務合約  
 服務合約就是提供下列資訊的陳述式：  
  
-   單一服務中作業的分組。  
  
-   依據所交換訊息的作業簽章。  
  
-   這些訊息的資料型別。  
  
-   作業的位置。  
  
-   用於支援與服務的成功通訊的特定通訊協定和序列化格式。  
  
 例如，採購單合約可能會有 `CreateOrder` 作業，該作業會接受訂單資訊輸入並傳回成功或失敗資訊 (包括訂單識別碼)。 它也可能會有 `GetOrderStatus` 作業，該作業會接受訂單識別碼並傳回訂單狀態資訊。 這類服務合約會指定：  
  
-   採購單合約由 `CreateOrder` 和 `GetOrderStatus` 作業組成。  
  
-   這些作業擁有指定的輸入訊息和輸出訊息。  
  
-   這些訊息可以包含的資料。  
  
-   成功處理訊息時所需要之通訊基礎結構的分類聲明。 例如，這些詳細資訊包含在建立成功通訊時是否需要安全性及安全性的格式為何。  
  
 若要傳達這類應用程式在其他平台 （包括非 Microsoft 平台） 上的資訊，XML 服務合約會公開以標準 XML 格式，例如[Web 服務描述語言 (WSDL)](https://go.microsoft.com/fwlink/?LinkId=87004)並[XML 結構描述 (XSD)](https://go.microsoft.com/fwlink/?LinkId=87005)，其他項目。 大多數平台的開發人員都可以使用這項公開的合約資訊來建立可以和服務進行通訊的應用程式，除了因為他們了解規格語言，更因為這些語言已設計成可透過描述服務所支援的公開形式、格式和通訊協定來達到互通性。 如需有關 WCF 如何處理這類資訊的詳細資訊，請參閱[中繼資料](../../../../docs/framework/wcf/feature-details/metadata.md)。  
  
 合約能夠以多種方式表示，但 WSDL 和 XSD 卻是能夠以可存取方式來描述服務的絕佳語言，這兩種語言很難直接使用，甚至在任何情況下，它們只能是服務的描述，而不是服務合約的實作。 因此，WCF 應用程式使用 managed 的屬性、 介面和類別定義的結構和實作的服務。  
  
 可以轉換產生 managed 類型中定義的合約 (也稱為*匯出*) 做為中繼資料 — WSDL 和 XSD — 時所需的用戶端或其他服務實作者，特別是在其他平台上的。 其結果便是產生一個簡單扼要的程式設計模型，而這個模型可以使用公開中繼資料描述給任何用戶端應用程式。 WCF，會自動執行必要的轉換服務合約型別系統之 XML 類型系統可以保留的基礎 SOAP 訊息，例如傳輸和安全性的相關資訊，詳細資料。  
  
 如需有關如何設計合約的詳細資訊，請參閱 < [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md)。 如需有關如何實作合約的詳細資訊，請參閱 < [Implementing Service Contracts](../../../../docs/framework/wcf/implementing-service-contracts.md)。  
  
 此外，WCF 也提供開發完全在訊息層級的服務合約的能力。 如需有關如何開發訊息層級的服務合約的詳細資訊，請參閱[Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)。 如需有關如何開發服務在非 SOAP XML 的詳細資訊，請參閱[與 POX 應用程式的互通性](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md)。  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>瞭解需求的階層架構  
 服務合約可將作業分組、指定 MEP、訊息類型，以及這些訊息所包含的資料型別，並指出實作必須擁有以支援合約的執行階段行為類別 (例如，合約可能會要求加密及簽署訊息)。 不過，服務合約本身並不會清楚地指定如何達到這些需求，而只會指定必須達到這些需求。 採用何種加密類型或訊息的簽署方式，將依實作以及相容服務之組態而有不同。  
  
 請注意，合約需要服務合約實作和執行階段組態中的某些項目才能新增行為。 必須符合才能公開服務提供使用的一組需求，是採用前一組需求來做為建置基礎。 如果合約有提出實作需求，則實作可能會需要更多的組態和繫結程序才能夠讓服務執行。 最後，主應用程式 (Host Application) 也必須支援服務組態和繫結程序所新增的任何需求。  
  
 這加總的需求程序是很重要要牢記在心，同時設計、 實作、 設定及裝載您的 Windows Communication Foundation (WCF) 服務應用程式。 例如，合約可以指定必須支援某個工作階段。 若是如此，您就必須將繫結程序設定成可支援該合約需求，否則服務實作將無法運作。 或者，如果您的服務需要整合式 Windows 驗證而且已裝載於網際網路資訊服務 (IIS)，則服務所在的 Web 應用程式必須啟用整合式 Windows 驗證並關閉匿名支援。 如需有關之功能和影響的不同服務主應用程式類型的詳細資訊，請參閱[Hosting](../../../../docs/framework/wcf/feature-details/hosting.md)。  
  
## <a name="see-also"></a>另請參閱

- [端點：位址、繫結和合約](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [設計服務合約](../../../../docs/framework/wcf/designing-service-contracts.md)
- [實作服務合約](../../../../docs/framework/wcf/implementing-service-contracts.md)

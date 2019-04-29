---
title: 設計與實作服務
ms.date: 03/30/2017
helpviewer_keywords:
- defining service contracts [WCF]
ms.assetid: 036fae20-7c55-4002-b71d-ac4466e167a3
ms.openlocfilehash: ad7e713ac4cbbe5bf227f4ab93e8f88684dcb0d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785017"
---
# <a name="designing-and-implementing-services"></a>設計與實作服務
本節將說明如何定義及實作 WCF 合約。 服務合約會指定端點與外界溝通的內容。 更具體來說，這是關於一組會組織到基本訊息交換模式 (MEP) 之特定訊息的聲明，而這些交換模式包括要求/回覆、單向和雙工。 如果服務合約為一組邏輯相關的訊息交換，則服務作業就是單一的訊息交換。 例如，`Hello` 作業一定會明確地接收一個訊息 (這樣呼叫端才能宣告歡迎畫面)，但卻不一定會傳回訊息 (需視作業的禮節而定)。  
  
 如需合約以及其他核心 Windows Communication Foundation (WCF) 概念的詳細資訊，請參閱[基本 Windows Communication Foundation 的概念](../../../docs/framework/wcf/fundamental-concepts.md)。 本主題將著重於讓您了解服務合約。 如需如何建置使用服務合約連線到服務的用戶端的詳細資訊，請參閱[WCF Client Overview](../../../docs/framework/wcf/wcf-client-overview.md)。  
  
## <a name="overview"></a>總覽  
 本主題提供設計與實作 WCF 服務的高層級概念方向。 副標題則提供設計和實作之細節的詳細資訊。 設計和實作之前 WCF 應用程式，建議您：  
  
- 瞭解服務合約是什麼、如何使用它，以及如何建立它。  
  
- 瞭解合約會聲明執行階段組態或裝載環境不一定會支援的最低需求。  
  
## <a name="service-contracts"></a>服務合約  
 服務合約會指定下列項目：  
  
- 合約所公開的作業。  
  
- 依據所交換訊息的作業簽章。  
  
- 這些訊息的資料型別。  
  
- 作業的位置。  
  
- 用於支援與服務的成功通訊的特定通訊協定和序列化格式。  
  
 例如，採購單合約可能會有 `CreateOrder` 作業，該作業會接受訂單資訊輸入並傳回成功或失敗資訊 (包括訂單識別碼)。 它也可能會有 `GetOrderStatus` 作業，該作業會接受訂單識別碼並傳回訂單狀態資訊。 這類服務合約會指定：  
  
1. 採購單合約由 `CreateOrder` 和 `GetOrderStatus` 作業組成。  
  
2. 這些作業擁有指定的輸入訊息和輸出訊息。  
  
3. 這些訊息可以包含的資料。  
  
4. 成功處理訊息時所需要之通訊基礎結構的分類聲明。 例如，這些詳細資訊包含在建立成功通訊時是否需要安全性及安全性的格式為何。  
  
 若要傳達這類其他應用程式在許多平台 （包括非 Microsoft 平台） 上的資訊，XML 服務合約會公開以標準 XML 格式，例如[Web 服務描述語言](https://go.microsoft.com/fwlink/?LinkId=94952)(WSDL) 和[XML 結構描述](https://go.microsoft.com/fwlink/?LinkId=94953)(XSD)，其他項目。 大多數平台的開發人員都可以使用這項公開的合約資訊來建立可以和服務進行通訊的應用程式，除了因為他們了解規格語言，更因為這些語言已設計成可透過描述服務所支援的公開形式、格式和通訊協定來達到互通性。 如需有關 WCF 如何處理這類資訊的詳細資訊，請參閱[中繼資料](../../../docs/framework/wcf/feature-details/metadata.md)。  
  
 合約能夠以多種方式表示，但 WSDL 和 XSD 卻是能夠以可存取方式來描述服務的絕佳語言，這兩種語言很難直接使用，而且只能建立服務描述，而不能建立服務合約實作。 因此，WCF 應用程式使用 managed 的屬性、 介面和類別來定義服務的結構並實作它。  
  
 可以是 managed 類型中定義的產生合約*匯出*做為中繼資料 — WSDL 和 XSD — 時所需的用戶端或其他服務實作器。 其結果便是產生一個簡單扼要的程式設計模型，而這個模型可以使用公開中繼資料描述給任何用戶端應用程式。 WCF，會自動執行必要的轉換服務合約型別系統之 XML 類型系統可以保留的基礎 SOAP 訊息、 傳輸和安全性的相關資訊，並依此類推，詳細資料。  
  
 如需有關如何設計合約的詳細資訊，請參閱 < [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md)。 如需有關如何實作合約的詳細資訊，請參閱 < [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md)。  
  
### <a name="messages-up-front-and-center"></a>最新的訊息  
 如果您已經習慣遠端程序呼叫 (RPC) 樣式的方法簽章，那麼使用 Managed 的介面、類別和方法來建立服務作業模型將更為簡單，此時傳遞參數至方法及接收傳回值是物件或其他類型程式碼之要求功能的一般形式。 例如，程式設計人員使用 managed 語言，例如 Visual Basic 和C++COM 可以套用其專業知識的 RPC 樣式方法 （不論使用物件或介面） 的 WCF 服務合約建立而不會遇到的問題在 RPC 樣式分散式物件系統。 服務方向除了提供鬆散耦合、訊息導向之程式設計的優點，同時保留簡易且熟悉的 RPC 程式設計經驗。  
  
 有許多程式設計人員更熟悉使用訊息導向的應用程式開發介面，例如 Microsoft MSMQ 之類的訊息佇列、.NET Framework 中的 <xref:System.Messaging> 命名空間 (Namespace)，或在 HTTP 要求中傳送非結構化的 XML，以上只是略舉部分例子。 如需在訊息層級進行程式設計的詳細資訊，請參閱[Using Message Contracts](../../../docs/framework/wcf/feature-details/using-message-contracts.md)，[服務通道層級程式設計](../../../docs/framework/wcf/extending/service-channel-level-programming.md)，和[與 POX 應用程式互通性](../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>瞭解需求的階層架構  
 服務合約可將作業分組、指定訊息交換模式、訊息類型，以及這些訊息所包含的資料型別，並指出實作必須擁有以支援合約的執行階段行為類別 (例如，合約可能會要求加密及簽署訊息)。 服務合約本身並不會清楚地指定如何達到這些需求，而只會指定必須達到這些需求。 加密類型或簽署訊息的方式取決於實作以及相容性服務的組態。  
  
 請注意，合約需要服務合約實作和執行階段組態中的某些項目才能新增行為。 必須符合才能公開服務提供使用的一組需求，是採用前一組需求來做為建置基礎。 如果合約有提出實作需求，則實作可能會需要更多的組態和繫結程序才能夠讓服務執行。 最後，主應用程式 (Host Application) 也必須支援服務組態和繫結程序所新增的任何需求。  
  
 這加總的需求程序是很重要要牢記在心，同時設計、 實作、 設定及裝載 Windows Communication Foundation (WCF) 服務應用程式。 例如，合約可以指定必須支援某個工作階段。 若是如此，您就必須將繫結程序設定成可支援該合約需求，否則服務實作將無法運作。 或者，如果您的服務需要 Windows 整合式驗證而且已裝載於網際網路資訊服務 (IIS)，則服務所在的 Web 應用程式必須啟用 Windows 整合式驗證並關閉匿名支援。 如需有關之功能和影響的不同服務主應用程式類型的詳細資訊，請參閱[裝載的服務](../../../docs/framework/wcf/hosting-services.md)。  
  
## <a name="see-also"></a>另請參閱

- [設計服務合約](../../../docs/framework/wcf/designing-service-contracts.md)
- [履行服務合約](../../../docs/framework/wcf/implementing-service-contracts.md)

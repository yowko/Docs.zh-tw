---
title: "設計與實作服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- defining service contracts [WCF]
ms.assetid: 036fae20-7c55-4002-b71d-ac4466e167a3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b6d5a2dfb4db1d57f60e4c7f8cf3300b766402e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="designing-and-implementing-services"></a>設計與實作服務
這個區段會顯示如何定義及實作[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]合約。 服務合約會指定端點與外界溝通的內容。 更具體來說，這是關於一組會組織到基本訊息交換模式 (MEP) 之特定訊息的聲明，而這些交換模式包括要求/回覆、單向和雙工。 如果服務合約為一組邏輯相關的訊息交換，則服務作業就是單一的訊息交換。 例如，`Hello` 作業一定會明確地接收一個訊息 (這樣呼叫端才能宣告歡迎畫面)，但卻不一定會傳回訊息 (需視作業的禮節而定)。  
  
 如需合約和其他核心[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]概念，請參閱[基本 Windows Communication Foundation 概念](../../../docs/framework/wcf/fundamental-concepts.md)。 本主題將著重於讓您了解服務合約。 如需如何建置用戶端用來連接到服務的服務合約的詳細資訊，請參閱[WCF 用戶端概觀](../../../docs/framework/wcf/wcf-client-overview.md)。  
  
## <a name="overview"></a>總覽  
 本主題會提供在設計和實作 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務時的高層級概念方向。 副標題則提供設計和實作之細節的詳細資訊。 在設計及實作您的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 應用程式之前，建議您先：  
  
-   瞭解服務合約是什麼、如何使用它，以及如何建立它。  
  
-   瞭解合約會聲明執行階段組態或裝載環境不一定會支援的最低需求。  
  
## <a name="service-contracts"></a>服務合約  
 服務合約會指定下列項目：  
  
-   合約所公開的作業。  
  
-   依據所交換訊息的作業簽章。  
  
-   這些訊息的資料型別。  
  
-   作業的位置。  
  
-   用於支援與服務的成功通訊的特定通訊協定和序列化格式。  
  
 例如，採購單合約可能會有 `CreateOrder` 作業，該作業會接受訂單資訊輸入並傳回成功或失敗資訊 (包括訂單識別碼)。 它也可能會有 `GetOrderStatus` 作業，該作業會接受訂單識別碼並傳回訂單狀態資訊。 這類服務合約會指定：  
  
1.  採購單合約由 `CreateOrder` 和 `GetOrderStatus` 作業組成。  
  
2.  這些作業擁有指定的輸入訊息和輸出訊息。  
  
3.  這些訊息可以包含的資料。  
  
4.  成功處理訊息時所需要之通訊基礎結構的分類聲明。 例如，這些詳細資訊包含在建立成功通訊時是否需要安全性及安全性的格式為何。  
  
 為了傳達這類資訊給其他應用程式在許多平台 （包括非 Microsoft 平台） 上，XML 服務合約公開以標準的 XML 格式，例如[Web 服務描述語言](http://go.microsoft.com/fwlink/?LinkId=94952)(WSDL) 和[XML 結構描述](http://go.microsoft.com/fwlink/?LinkId=94953)(XSD)，和其他項目。 大多數平台的開發人員都可以使用這項公開的合約資訊來建立可以和服務進行通訊的應用程式，除了因為他們了解規格語言，更因為這些語言已設計成可透過描述服務所支援的公開形式、格式和通訊協定來達到互通性。 如需有關如何[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]處理這種資訊，請參閱[中繼資料](../../../docs/framework/wcf/feature-details/metadata.md)。  
  
 合約能夠以多種方式表示，但 WSDL 和 XSD 卻是能夠以可存取方式來描述服務的絕佳語言，這兩種語言很難直接使用，而且只能建立服務描述，而不能建立服務合約實作。 因此，[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 應用程式會使用 Managed 屬性、介面和類別來定義服務結構並實作該服務。  
  
 產生 managed 型別中定義的合約可以是*匯出*做為中繼資料 — WSDL 和 XSD： 用戶端或其他服務實作器需要時。 其結果便是產生一個簡單扼要的程式設計模型，而這個模型可以使用公開中繼資料描述給任何用戶端應用程式。 基礎 SOAP 訊息的詳細資訊、傳輸和安全性相關資訊等資料可以留給 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]，這個應用程式會在必要時自動在服務合約類型系統和 XML 類型系統之間來回執行轉換。  
  
 如需有關如何設計合約的詳細資訊，請參閱[設計服務合約](../../../docs/framework/wcf/designing-service-contracts.md)。 如需實作合約的詳細資訊，請參閱[實作服務合約](../../../docs/framework/wcf/implementing-service-contracts.md)。  
  
### <a name="messages-up-front-and-center"></a>最新的訊息  
 如果您已經習慣遠端程序呼叫 (RPC) 樣式的方法簽章，那麼使用 Managed 的介面、類別和方法來建立服務作業模型將更為簡單，此時傳遞參數至方法及接收傳回值是物件或其他類型程式碼之要求功能的一般形式。 例如，使用 Managed 語言 (例如 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 和 C++ COM) 的程式設計人員可以在建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務合約時應用他們對於 RPC 樣式方法 (不論使用物件或介面) 的知識，而不會遇到 RPC 樣式分散式物件系統的固有問題。 服務方向除了提供鬆散耦合、訊息導向之程式設計的優點，同時保留簡易且熟悉的 RPC 程式設計經驗。  
  
 有許多程式設計人員更熟悉使用訊息導向的應用程式開發介面，例如 Microsoft MSMQ 之類的訊息佇列、.NET Framework 中的 <xref:System.Messaging> 命名空間 (Namespace)，或在 HTTP 要求中傳送非結構化的 XML，以上只是略舉部分例子。 如需在訊息層級的程式設計的詳細資訊，請參閱[使用訊息合約](../../../docs/framework/wcf/feature-details/using-message-contracts.md)，[服務通道層級程式設計](../../../docs/framework/wcf/extending/service-channel-level-programming.md)，和[與 POX 應用程式互通性](../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>瞭解需求的階層架構  
 服務合約可將作業分組、指定訊息交換模式、訊息類型，以及這些訊息所包含的資料型別，並指出實作必須擁有以支援合約的執行階段行為類別 (例如，合約可能會要求加密及簽署訊息)。 服務合約本身並不會清楚地指定如何達到這些需求，而只會指定必須達到這些需求。 加密類型或簽署訊息的方式取決於實作以及相容性服務的組態。  
  
 請注意，合約需要服務合約實作和執行階段組態中的某些項目才能新增行為。 必須符合才能公開服務提供使用的一組需求，是採用前一組需求來做為建置基礎。 如果合約有提出實作需求，則實作可能會需要更多的組態和繫結才能夠讓服務執行。 最後，主應用程式 (Host Application) 也必須支援服務組態和繫結所新增的任何需求。  
  
 在設計、實作、設定和裝載 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務應用程式時，必須特別注意這項新增的需求程序。 例如，合約可以指定必須支援某個工作階段。 若是如此，您就必須將繫結程序設定成可支援該合約需求，否則服務實作將無法運作。 或者，如果您的服務需要 Windows 整合式驗證而且已裝載於網際網路資訊服務 (IIS)，則服務所在的 Web 應用程式必須啟用 Windows 整合式驗證並關閉匿名支援。 如需不同的服務主機應用程式類型的影響，功能的詳細資訊，請參閱[裝載服務](../../../docs/framework/wcf/hosting-services.md)。  
  
## <a name="see-also"></a>請參閱  
 [設計服務合約](../../../docs/framework/wcf/designing-service-contracts.md)  
 [履行服務合約](../../../docs/framework/wcf/implementing-service-contracts.md)

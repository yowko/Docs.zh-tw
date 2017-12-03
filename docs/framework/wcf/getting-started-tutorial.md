---
title: "使用者入門 Tutorial1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], getting started
- Windows Communication Foundation [WCF], getting started
- getting started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
caps.latest.revision: "47"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 649fc2572e809238977ca3deb5740ada2dd5dc14
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="getting-started-tutorial"></a>快速入門教學課程
本節所包含的主題主要是讓您快速獲得 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 程式設計經驗。 每個主題已設計成依本主題結尾的清單順序完成。 完成這個入門課程之後，您將對建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務與用戶端應用程式所需的步驟有初步的了解。 服務會公開一個或多個端點，而其中每個端點都會公開一項或多項服務作業。 *端點*服務的指定位置可以找到服務，位址的繫結，其中包含說明定義功能的合約與服務，用戶端必須之間的通訊資訊提供服務給其用戶端。  
  
 在您逐步執行本教學課程中各主題的程序之後，您將會有執行中的服務和呼叫服務的用戶端。 前面三個主題說明如何定義服務合約、如何實作服務合約以及如何裝載服務。 建立的這個服務是在主控台應用程式中自我裝載的服務。 服務也可以在網際網路資訊服務 (IIS) 之下進行裝載。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]如何執行這項操作，請參閱[How to： 將 WCF 服務裝載於 IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。 服務是在程式碼中進行設定的，但是也可以在組態檔中設定。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]使用組態檔看到[設定服務使用組態檔](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)。  
  
 後面三個主題將說明如何建立用戶端 Proxy、設定用戶端應用程式，以及使用用戶端 Proxy 來呼叫服務所公開的服務作業。 服務會發行定義用戶端應用程式與服務進行通訊所需之資訊的中繼資料。 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 會自動化存取這個中繼資料的程序，並用它來建構和設定服務的用戶端應用程式。 如果您不使用[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]，您可以使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來建構和設定服務的用戶端應用程式。  
  
 本節中的所有主題都假設您是使用 Visual Studio 2011 做為開發環境。 如果您使用的是其他開發環境，請忽略特定的 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] 指示。  
  
> [!NOTE]
>  如果您正在[!INCLUDE[wv](../../../includes/wv-md.md)]或更新版本的 Windows 作業系統，您必須啟動[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]先移至 [開始] 功能表，以滑鼠右鍵按一下 Visual Studio 2011，再選取**系統管理員身分執行**。 若要一律以您可以建立快速鍵，以滑鼠右鍵按一下該快速鍵，選取屬性，選取系統管理員身分啟動 Visual Studio 2011**相容性**索引標籤，然後檢查**以系統管理員身分執行此程式**核取方塊。 當您使用此快速鍵啟動 Visual Studio 2011 時，以後就會固定以系統管理員身分執行。  
  
 範例應用程式會將下載到您的硬碟和執行，請參閱中的主題[Windows Communication Foundation 範例](http://msdn.microsoft.com/en-us/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)。 如本主題中，特別是，請參閱[入門](../../../docs/framework/wcf/samples/getting-started-sample.md)。  
  
 如需建立服務和用戶端相關的深入資訊，請參閱[基本 WCF 程式設計](../../../docs/framework/wcf/basic-wcf-programming.md)。  
  
## <a name="in-this-section"></a>本章節內容  
 [如何：定義服務合約](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 說明如何利用使用者定義的介面來建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 合約。 合約會定義服務所公開的功能。  
  
 [如何：履行服務合約](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 說明如何實作服務合約。 一旦定義了合約，就必須透過服務類別加以實作。  
  
 [如何：裝載及執行基本服務](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)  
 說明如何在程式碼中設定服務的端點，以及如何在主控台應用程式中裝載服務。 如果要成為作用中的服務，必須在執行階段環境中設定與裝載服務。 此環境會建立服務並控制其內容與存留期。  
  
 [如何：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 說明如何從 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務擷取用來建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端 Proxy 的中繼資料。 這個程序會使用 Visual Studio 2011 中的 [加入服務參考] 功能。  
  
 [如何：設定用戶端](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
 說明如何設定 WCF 用戶端。設定用戶端時，需要指定用戶端用來存取服務的端點。  
  
 [如何：使用用戶端](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)  
 說明如何使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端 Proxy 來叫用服務作業。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
## <a name="related-sections"></a>相關章節  
 [Windows Communication Foundation 範例](http://msdn.microsoft.com/en-us/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
  
 [基本程式設計週期](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
## <a name="see-also"></a>另請參閱  
 [概念性概觀](../../../docs/framework/wcf/conceptual-overview.md)  
 [文件指南](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [什麼是 Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [WCF 功能詳細資料](../../../docs/framework/wcf/feature-details/index.md)

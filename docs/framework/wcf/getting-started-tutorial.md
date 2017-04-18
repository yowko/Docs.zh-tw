---
title: "快速入門教學課程 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "使用者入門 [WCF]"
  - "WCF [WCF], 使用者入門"
  - "Windows Communication Foundation [WCF], 使用者入門"
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
caps.latest.revision: 47
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 47
---
# 快速入門教學課程
本節所包含的主題主要是讓您快速獲得 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 程式設計經驗。  每個主題已設計成依本主題結尾的清單順序完成。  完成這個入門課程之後，您將對建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務與用戶端應用程式所需的步驟有初步的了解。  服務會公開一個或多個端點，而其中每個端點都會公開一項或多項服務作業。  服務的「*端點*」\(Endpoint\) 會指定可以找到服務的位址、包含說明用戶端必須如何與服務通訊之資訊的繫結，以及定義服務為其用戶端提供之功能的合約。  
  
 在您逐步執行本教學課程中各主題的程序之後，您將會有執行中的服務和呼叫服務的用戶端。  前面三個主題說明如何定義服務合約、如何實作服務合約以及如何裝載服務。  建立的這個服務是在主控台應用程式中自我裝載的服務。  服務也可以在網際網路資訊服務 \(IIS\) 之下進行裝載。  [!INCLUDE[crabout](../../../includes/crabout-md.md)]如何執行這項工作的詳細資訊，請參閱 [HOW TO：在 IIS 中裝載 WCF 服務](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。  服務是在程式碼中進行設定的，但是也可以在組態檔中設定。  [!INCLUDE[crabout](../../../includes/crabout-md.md)]使用組態檔的詳細資訊，請參閱 [使用組態檔設定服務](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)。  
  
 後面三個主題將說明如何建立用戶端 Proxy、設定用戶端應用程式，以及使用用戶端 Proxy 來呼叫服務所公開的服務作業。  服務會發行定義用戶端應用程式與服務進行通訊所需之資訊的中繼資料。  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 會自動化存取這個中繼資料的程序，並用它來建構和設定服務的用戶端應用程式。  如果您沒有使用 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]，可以使用 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 來構建和設定服務的用戶端應用程式。  
  
 本節中的所有主題都假設您是使用 Visual Studio 2011 做為開發環境。  如果您使用的是其他開發環境，請忽略特定的 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] 指示。  
  
> [!NOTE]
>  如果您執行的是 [!INCLUDE[wv](../../../includes/wv-md.md)] 或更新的 Windows 作業系統版本，就必須啟動 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]，方法是移到 \[開始\] 功能表，然後以滑鼠右鍵按一下 \[Visual Studio 2011\] 並選取 \[**以系統管理員身分執行**\]。  若要固定以系統管理員身分啟動 Visual Studio 2011，您可以建立快速鍵，然後以滑鼠右鍵按一下該快速鍵，接著依序選取內容、\[**相容性**\] 索引標籤，再核取 \[**以系統管理員身分執行此程式**\] 核取方塊。  當您使用此快速鍵啟動 Visual Studio 2011 時，以後就會固定以系統管理員身分執行。  
  
 如需可以下載至硬碟並執行的應用程式範例，請參閱 [Windows Communication Foundation Samples](http://msdn.microsoft.com/zh-tw/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)中的主題。  至於此主題的應用程式範例，請特別參閱[使用者入門](../../../docs/framework/wcf/samples/getting-started-sample.md)。  
  
 如需建立服務與用戶端的深入資訊，請參閱[基本 WCF 程式設計](../../../docs/framework/wcf/basic-wcf-programming.md)。  
  
## 在本節中  
 [HOW TO：定義服務合約](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 說明如何利用使用者定義的介面來建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 合約。  合約會定義服務所公開的功能。  
  
 [HOW TO：實作服務合約](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 說明如何實作服務合約。  一旦定義了合約，就必須透過服務類別加以實作。  
  
 [HOW TO：裝載和執行基本服務](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)  
 說明如何在程式碼中設定服務的端點，以及如何在主控台應用程式中裝載服務。  如果要成為作用中的服務，必須在執行階段環境中設定與裝載服務。  此環境會建立服務並控制其內容與存留期。  
  
 [HOW TO：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 說明如何從 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務擷取用來建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端 Proxy 的中繼資料。  這個程序會使用 Visual Studio 2011 中的 \[加入服務參考\] 功能。  
  
 [HOW TO：設定用戶端](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
 說明如何設定 WCF 用戶端。設定用戶端時，需要指定用戶端用來存取服務的端點。  
  
 [HOW TO：使用用戶端](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)  
 說明如何使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端 Proxy 來叫用服務作業。  
  
## 參考  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
## 相關章節  
 [Windows Communication Foundation Samples](http://msdn.microsoft.com/zh-tw/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
  
 [基本程式設計週期](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
## 請參閱  
 [概觀說明](../../../docs/framework/wcf/conceptual-overview.md)   
 [文件指南](../../../docs/framework/wcf/guide-to-the-documentation.md)   
 [何謂 Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)   
 [WCF 功能詳細資料](../../../docs/framework/wcf/feature-details/index.md)
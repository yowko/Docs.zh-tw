---
title: "HOW TO：在 Managed 應用程式中裝載 WCF 服務 | Microsoft Docs"
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
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
caps.latest.revision: 42
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 42
---
# HOW TO：在 Managed 應用程式中裝載 WCF 服務
若要將服務裝載於 Managed 應用程式中，請將服務的程式碼嵌入 Managed 應用程式的程式碼，再以命令式程式碼或透過組態以宣告方式定義服務的端點 \(亦可使用預設端點\)，然後建立 <xref:System.ServiceModel.ServiceHost> 的執行個體。  
  
 若要開始接收訊息，請呼叫 <xref:System.ServiceModel.ServiceHost> 上的 <xref:System.ServiceModel.ICommunicationObject.Open%2A>。這樣會建立並開啟服務的接聽項。用這種方式來裝載服務一般稱為「自我裝載」，因為 Managed 應用程式會自行執行裝載工作。若要關閉服務，請呼叫 <xref:System.ServiceModel.ServiceHost> 上的 <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=fullName>。  
  
 您也可以透過 Managed Windows 服務、網際網路資訊服務 \(IIS\)，或是 Windows Process Activation Service \(WAS\) 來裝載服務。[!INCLUDE[crabout](../../../includes/crabout-md.md)]服務的裝載選項的詳細資訊，請參閱[裝載服務](../../../docs/framework/wcf/hosting-services.md)。  
  
 將服務裝載在 Managed 應用程式中是最有彈性的選項，因為這麼做只需要部署最基本基礎結構。[!INCLUDE[crabout](../../../includes/crabout-md.md)]將服務裝載在 Managed 應用程式的詳細資訊，請參閱[在 Managed 應用程式中裝載](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)。  
  
 下列程序示範如何在主控台應用程式中實作自我裝載的服務。  
  
### 建立自我裝載服務  
  
1.  開啟 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]，再依序選取 \[**檔案**\] 功能表上的 \[**新增**\] 和 \[**專案**\]。  
  
2.  依序選取 \[**已安裝的範本**\] 清單中的 \[**Visual C\#**\] 和 \[**Windows**\] 或是 \[**Visual Basic**\] 和 \[**Windows**\]。視您如何設定 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]，這些項目其一或兩者在 \[**已安裝的範本**\] 清單中可能位於 \[**其他語言**\] 節點底下。  
  
3.  選取 \[**Windows**\] 清單中的 \[**主控台應用程式**\]。在 \[**名稱**\] 方塊中輸入 `SelfHost`，然後按一下 \[**確定**\]。  
  
4.  以滑鼠右鍵按一下 \[**方案總管**\] 中的 \[**SelfHost**\]，然後選取 \[**加入參考**\]。選取 \[**.NET**\] 索引標籤上的 \[**System.ServiceModel**\]，然後按一下 \[**確定**\]。  
  
    > [!TIP]
    >  如果看不到 \[**方案總管**\] 視窗，請選取 \[**檢視**\] 功能表上的 \[**方案總管**\]。  
  
5.  按兩下 \[**方案總管**\] 中的 \[**Program.cs**\] 或 \[**Module1.vb**\]，開啟檔案的程式碼視窗 \(如果尚未開啟\)。在檔案最上方加入下列陳述式。  
  
     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]  
  
6.  定義與實作服務合約。本範例會定義 `HelloWorldService` 以根據輸入服務的資料傳回訊息。  
  
     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]  
  
    > [!NOTE]
    >  [!INCLUDE[crabout](../../../includes/crabout-md.md)]如何定義與實作服務介面的詳細資訊，請參閱 [HOW TO：定義服務合約](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)及 [HOW TO：實作服務合約](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)。  
  
7.  在 `Main` 方法頂端使用服務的基底位址，建立 <xref:System.Uri> 類別的執行個體。  
  
     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]  
  
8.  建立 <xref:System.ServiceModel.ServiceHost> 類別的執行個體，並將代表服務類型與基底位址統一資源識別元 \(URI\) 的 <xref:System.Type> 傳入 [ServiceHost\(Type, Uri\<xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>。啟用中繼資料發行，然後呼叫 <xref:System.ServiceModel.ServiceHost> 的 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法初始化服務並準備接收訊息。  
  
     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]  
  
    > [!NOTE]
    >  本範例將使用預設端點，所以這項服務不需要組態檔。如果沒有設定端點，執行階段就會針對服務所實作的每份服務合約，為每個基底位址各建立一個端點。[!INCLUDE[crabout](../../../includes/crabout-md.md)]預設端點的詳細資訊，請參閱[簡化的組態](../../../docs/framework/wcf/simplified-configuration.md)和[WCF 服務的簡化組態](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
9. 按 CTRL\+SHIFT\+B 建置方案。  
  
### 若要測試服務  
  
1.  按 Ctrl \+ F5 執行服務。  
  
2.  開啟 **WCF 測試用戶端**。  
  
    > [!TIP]
    >  若要開啟 \[**WCF 測試用戶端**\]，請開啟 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 命令提示字元並執行 **WcfTestClient.exe**。  
  
3.  選取 \[**檔案**\] 功能表上的 \[**新增服務**\]。  
  
4.  在位址方塊中輸入 `http://localhost:8080/hello`，然後按一下 \[**確定**\]。  
  
    > [!TIP]
    >  請確認服務正在執行中，否則這個步驟會失敗。若您已從程式碼變更了基底位址，即應在此步驟中使用修改後的基底位址。  
  
5.  按兩下 \[**我的服務專案**\] 節點底下的 \[**SayHello**\]。在 \[**要求**\] 清單中的 \[**值**\] 欄內輸入您的名稱，然後按一下 \[**叫用**\]。回覆訊息隨即出現在 \[**回應**\] 清單中。  
  
## 範例  
 下列範例會建立 <xref:System.ServiceModel.ServiceHost> 物件來裝載型別為 `HelloWorldService` 的服務，然後呼叫 <xref:System.ServiceModel.ServiceHost> 的 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法。基底位址由程式碼提供、中繼資料發行已啟用，而且將使用預設端點。  
  
 [!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
 [!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]  
  
## 請參閱  
 <xref:System.Uri>   
 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>   
 <xref:System.Configuration.ConfigurationManager>   
 [HOW TO：在 IIS 中裝載 WCF 服務](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)   
 [自我裝載](../../../docs/framework/wcf/samples/self-host.md)   
 [裝載服務](../../../docs/framework/wcf/hosting-services.md)   
 [HOW TO：定義服務合約](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)   
 [HOW TO：實作服務合約](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)   
 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)   
 [使用繫結來設定服務和用戶端](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)   
 [系統提供的繫結](../../../docs/framework/wcf/system-provided-bindings.md)
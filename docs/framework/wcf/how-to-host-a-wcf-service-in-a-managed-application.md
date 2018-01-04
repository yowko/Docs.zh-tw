---
title: "HOW TO：在 Managed 應用程式中裝載 WCF 服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6491faa6134c1e80e07294d8f888200c04fa8704
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-wcf-service-in-a-managed-application"></a>HOW TO：在 Managed 應用程式中裝載 WCF 服務
若要將服務裝載於 Managed 應用程式中，請將服務的程式碼嵌入 Managed 應用程式的程式碼，再以命令式程式碼或透過組態以宣告方式定義服務的端點 (亦可使用預設端點)，然後建立 <xref:System.ServiceModel.ServiceHost> 的執行個體。  
  
 若要開始接收訊息，請呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 上的 <xref:System.ServiceModel.ServiceHost>。 這樣會建立並開啟服務的接聽項。 用這種方式來裝載服務一般稱為「自我裝載」，因為 Managed 應用程式會自行執行裝載工作。 若要關閉服務，請呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> 上的 <xref:System.ServiceModel.ServiceHost>。  
  
 服務也可以裝載在 Managed Windows 服務、Internet Information Services (IIS) 或 Windows Process Activation Service (WAS) 中。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]裝載服務的選項，請參閱[裝載服務](../../../docs/framework/wcf/hosting-services.md)。  
  
 將服務裝載在 Managed 應用程式中是最有彈性的選項，因為這麼做只需要部署最基本基礎結構。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]裝載在 managed 應用程式的服務，請參閱[受管理的應用程式中裝載](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)。  
  
 下列程序示範如何在主控台應用程式中實作自我裝載的服務。  
  
### <a name="to-create-a-self-hosted-service"></a>若要建立自我裝載服務  
  
1.  開啟[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]選取**新增**，**專案...**從**檔案**功能表。  
  
2.  在**已安裝的範本**清單中，選取**Visual C#**， **Windows**或**Visual Basic**， **Windows**. 取決於您[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]設定、 一個或這兩種可能會顯示在**其他語言**節點**已安裝的範本**清單。  
  
3.  選取**主控台應用程式**從**Windows**清單。 型別`SelfHost`中**名稱**方塊，然後按一下**確定**。  
  
4.  以滑鼠右鍵按一下**SelfHost**中**方案總管] 中**選取**加入參考...**.選取**System.ServiceModel**從**.NET**索引標籤上，按一下 [**確定**。  
  
    > [!TIP]
    >  如果**方案總管 中**視窗未顯示，請選取**方案總管 中**從**檢視**功能表。  
  
5.  按兩下**Program.cs**或**Module1.vb**中**方案總管 中**開啟程式碼視窗中，如果它尚未開啟。 在檔案最上方加入下列陳述式。  
  
     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]  
  
6.  定義與實作服務合約。 本範例會定義 `HelloWorldService` 以根據輸入服務的資料傳回訊息。  
  
     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]  
  
    > [!NOTE]
    >  [!INCLUDE[crabout](../../../includes/crabout-md.md)]如何定義和實作服務介面，請參閱[如何： 定義服務合約](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)和[How to： 實作服務合約](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)。  
  
7.  在 `Main` 方法頂端使用服務的基底位址，建立 <xref:System.Uri> 類別的執行個體。  
  
     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]  
  
8.  建立 <xref:System.ServiceModel.ServiceHost> 類別的執行個體，並將代表服務型別與基底位址統一資源識別元 (URI) 的 <xref:System.Type> 傳入 <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>。 啟用中繼資料發行，然後呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 的 <xref:System.ServiceModel.ServiceHost> 方法初始化服務並準備接收訊息。  
  
     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]       
  
    > [!NOTE]
    >  本範例將使用預設端點，所以這項服務不需要組態檔。 如果沒有設定端點，執行階段就會針對服務所實作的每份服務合約，為每個基底位址各建立一個端點。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]預設端點，請參閱[簡化的組態](../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
9. 按下 CTRL+SHIFT+B 以建置方案。  
  
### <a name="to-test-the-service"></a>若要測試服務  
  
1.  按 Ctrl + F5 執行服務。  
  
2.  開啟**WCF 測試用戶端**。  
  
    > [!TIP]
    >  若要開啟**WCF 測試用戶端**，開啟[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]命令提示字元並執行**WcfTestClient.exe**。  
  
3.  選取**新增服務...**從**檔案**功能表。  
  
4.  型別`http://localhost:8080/hello`輸入地址 方塊，然後按一下**確定**。  
  
    > [!TIP]
    >  請確認服務正在執行中，否則這個步驟會失敗。 若您已從程式碼變更了基底位址，即應在此步驟中使用修改後的基底位址。  
  
5.  按兩下**SayHello**下**我的服務專案**節點。 輸入您的名稱到**值**中的資料行**要求**清單，然後按**Invoke**。 回覆訊息會出現在**回應**清單。  
  
## <a name="example"></a>範例  
 下列範例會建立 <xref:System.ServiceModel.ServiceHost> 物件來裝載型別為 `HelloWorldService` 的服務，然後呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 上的 <xref:System.ServiceModel.ServiceHost> 方法。 基底位址由程式碼提供、中繼資料發行已啟用，而且將使用預設端點。  
  
 [!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
 [!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Uri>  
 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>  
 <xref:System.Configuration.ConfigurationManager>  
 [如何：在 IIS 中裝載 WCF 服務](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [自我裝載](../../../docs/framework/wcf/samples/self-host.md)  
 [裝載服務](../../../docs/framework/wcf/hosting-services.md)  
 [如何：定義服務合約](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [如何：履行服務合約](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [使用繫結設定服務與用戶端](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [系統提供的繫結](../../../docs/framework/wcf/system-provided-bindings.md)

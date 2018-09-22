---
title: HOW TO：在 Managed 應用程式中裝載 WCF 服務
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: 131d99457427e0818f78076d987f550a99ad7cf0
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696284"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a>如何： 將 WCF 服務裝載於受管理的應用程式

若要將服務裝載於 Managed 應用程式中，請將服務的程式碼嵌入 Managed 應用程式的程式碼，再以命令式程式碼或透過組態以宣告方式定義服務的端點 (亦可使用預設端點)，然後建立 <xref:System.ServiceModel.ServiceHost> 的執行個體。

若要開始接收訊息，請呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 上的 <xref:System.ServiceModel.ServiceHost>。 這樣會建立並開啟服務的接聽項。 用這種方式來裝載服務一般稱為「自我裝載」，因為 Managed 應用程式會自行執行裝載工作。 若要關閉服務，請呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> 上的 <xref:System.ServiceModel.ServiceHost>。

服務也可以裝載在 Managed Windows 服務、Internet Information Services (IIS) 或 Windows Process Activation Service (WAS) 中。 如需有關如何裝載服務的選項的詳細資訊，請參閱[裝載的服務](../../../docs/framework/wcf/hosting-services.md)。

將服務裝載在 Managed 應用程式中是最有彈性的選項，因為這麼做只需要部署最基本基礎結構。 如需有關如何在受管理的應用程式中裝載服務的詳細資訊，請參閱 <<c0> [ 受管理的應用程式中裝載](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)。

下列程序示範如何在主控台應用程式中實作自我裝載的服務。

## <a name="create-a-self-hosted-service"></a>建立自我裝載的服務

1. 建立新的主控台應用程式：

   1. 開啟 Visual Studio，然後選取**的新** > **專案**從**檔案**功能表。

   2. 在 **已安裝的範本**清單中，選取**Visual C#** 或**Visual Basic**，然後選取**Windows Desktop**。

   3. 選取 **主控台應用程式**範本。 型別`SelfHost`中**名稱**方塊，然後選擇**確定**。

2. 以滑鼠右鍵按一下**SelfHost**中**方案總管**，然後選取**加入參考**。 選取  **System.ServiceModel**從 **.NET**索引標籤，然後選擇**確定**。

    > [!TIP]
    > 如果**方案總管**視窗未顯示，選取**方案總管**從**檢視**功能表。

3. 按兩下**Program.cs**或是**Module1.vb**中**方案總管 中**開啟在 程式碼 視窗中，如果它尚未開啟。 在檔案頂端新增下列陳述式：

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. 定義與實作服務合約。 本範例會定義 `HelloWorldService` 以根據輸入服務的資料傳回訊息。

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > 如需如何定義和實作服務介面的詳細資訊，請參閱[如何： 定義服務合約](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)並[如何： 實作服務合約](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)。

5. 在 `Main` 方法頂端使用服務的基底位址，建立 <xref:System.Uri> 類別的執行個體。

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. 建立 <xref:System.ServiceModel.ServiceHost> 類別的執行個體，並將代表服務型別與基底位址統一資源識別元 (URI) 的 <xref:System.Type> 傳入 <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>。 啟用中繼資料發行，然後呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 的 <xref:System.ServiceModel.ServiceHost> 方法初始化服務並準備接收訊息。

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > 本範例將使用預設端點，所以這項服務不需要組態檔。 如果沒有設定端點，執行階段就會針對服務所實作的每份服務合約，為每個基底位址各建立一個端點。 如需有關預設端點的詳細資訊，請參閱 < [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。

7. 按下**Ctrl**+**Shift**+**B**建置方案。

## <a name="test-the-service"></a>測試服務

1. 按下**Ctrl**+**F5**來執行服務。

2. 開啟**WCF 測試用戶端**。

    > [!TIP]
    > 若要開啟  **WCF 測試用戶端**，開啟適用於 Visual Studio 的開發人員命令提示字元並執行**WcfTestClient.exe**。

3. 選取 **新增服務**從**檔案**功能表。

4. 型別`http://localhost:8080/hello`輸入地址 方塊，然後按一下**確定**。

    > [!TIP]
    > 請確認服務正在執行中，否則這個步驟會失敗。 若您已從程式碼變更了基底位址，即應在此步驟中使用修改後的基底位址。

5. 按兩下**SayHello**下方**我的服務專案**節點。 輸入您的名稱到**值**中的資料行**要求**清單，然後按**Invoke**。

   回覆訊息會出現在**回應**清單。

## <a name="example"></a>範例

下列範例會建立 <xref:System.ServiceModel.ServiceHost> 物件來裝載型別為 `HelloWorldService` 的服務，然後呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 上的 <xref:System.ServiceModel.ServiceHost> 方法。 基底位址由程式碼提供、中繼資料發行已啟用，而且將使用預設端點。

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a>另請參閱

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [如何：在 IIS 中裝載 WCF 服務](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [自我裝載](../../../docs/framework/wcf/samples/self-host.md)
- [裝載服務](../../../docs/framework/wcf/hosting-services.md)
- [如何：定義服務合約](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [如何：履行服務合約](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [使用繫結設定服務與用戶端](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [系統提供的繫結](../../../docs/framework/wcf/system-provided-bindings.md)
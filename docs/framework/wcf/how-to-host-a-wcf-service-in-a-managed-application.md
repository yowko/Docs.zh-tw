---
title: HOW TO：在 Managed 應用程式中裝載 WCF 服務
description: 瞭解如何藉由建立自我裝載服務並加以測試，在受控應用程式中託管 WCF 服務。
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: 7d1d61b683f60a6c643d2a2f03d367a6ae6c6c15
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246164"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a>如何：在 managed 應用程式中裝載 WCF 服務

若要將服務裝載於 Managed 應用程式中，請將服務的程式碼嵌入 Managed 應用程式的程式碼，再以命令式程式碼或透過組態以宣告方式定義服務的端點 (亦可使用預設端點)，然後建立 <xref:System.ServiceModel.ServiceHost> 的執行個體。

若要開始接收訊息，請呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 上的 <xref:System.ServiceModel.ServiceHost>。 這樣會建立並開啟服務的接聽項。 用這種方式來裝載服務一般稱為「自我裝載」，因為 Managed 應用程式會自行執行裝載工作。 若要關閉服務，請呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> 上的 <xref:System.ServiceModel.ServiceHost>。

服務也可以裝載在 Managed Windows 服務、Internet Information Services (IIS) 或 Windows Process Activation Service (WAS) 中。 如需服務裝載選項的詳細資訊，請參閱[裝載服務](hosting-services.md)。

將服務裝載在 Managed 應用程式中是最有彈性的選項，因為這麼做只需要部署最基本基礎結構。 如需在 managed 應用程式中裝載服務的詳細資訊，請參閱[在 Managed 應用程式中裝載](./feature-details/hosting-in-a-managed-application.md)。

下列程序示範如何在主控台應用程式中實作自我裝載的服務。

## <a name="create-a-self-hosted-service"></a>建立自我裝載的服務

1. 建立新的主控台應用程式：

   1. 開啟 Visual Studio，然後**New**  >  從 [檔案] **File**功能表選取 [新增**專案**]。

   2. 在 [**安裝的範本**] 清單中，選取 [ **Visual c #** ] 或 [ **Visual Basic**]，然後選取 [ **Windows 桌面**]。

   3. 選取 [**主控台應用程式**] 範本。 `SelfHost`在 [**名稱**] 方塊中輸入，然後選擇 **[確定]**。

2. 以滑鼠右鍵按一下**方案總管**中的 [ **SelfHost** ]，然後選取 [**新增參考**]。 從 [ **.net** ] 索引標籤中選取 [ **system.servicemodel** ]，然後選擇 **[確定]**。

    > [!TIP]
    > 如果看不到 [**方案總管**] 視窗，請從 [ **View** ] 功能表中選取 [**方案總管**]。

3. 按兩下**方案總管**中的 [ **Program.cs** ] 或 [ **Module1** ]，在程式碼視窗中開啟它（如果尚未開啟）。 在檔案頂端新增下列語句：

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. 定義與實作服務合約。 本範例會定義 `HelloWorldService` 以根據輸入服務的資料傳回訊息。

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > 如需如何定義和執行服務介面的詳細資訊，請參閱[如何：定義服務合約](how-to-define-a-wcf-service-contract.md)和[如何：執行服務合約](how-to-implement-a-wcf-contract.md)。

5. 在 `Main` 方法頂端使用服務的基底位址，建立 <xref:System.Uri> 類別的執行個體。

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. 建立 <xref:System.ServiceModel.ServiceHost> 類別的執行個體，並將代表服務型別與基底位址統一資源識別元 (URI) 的 <xref:System.Type> 傳入 <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>。 啟用中繼資料發行，然後呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 的 <xref:System.ServiceModel.ServiceHost> 方法初始化服務並準備接收訊息。

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > 本範例將使用預設端點，所以這項服務不需要組態檔。 如果沒有設定端點，執行階段就會針對服務所實作的每份服務合約，為每個基底位址各建立一個端點。 如需預設端點的詳細資訊，請參閱[簡化](simplified-configuration.md)的設定和[WCF 服務的簡化](./samples/simplified-configuration-for-wcf-services.md)設定。

7. 按**Ctrl** + **Shift** + **B**以建立方案。

## <a name="test-the-service"></a>測試服務

1. 按**Ctrl** + **F5**執行服務。

2. 開啟 [ **WCF 測試用戶端**]。

    > [!TIP]
    > 若要開啟**WCF 測試用戶端**，請開啟 Visual Studio 的開發人員命令提示字元，然後執行**WcfTestClient.exe**。

3. 從 [檔案] 功能表**中選取**[**新增服務**]。

4. `http://localhost:8080/hello`在 [位址] 方塊中輸入，然後按一下 **[確定]**。

    > [!TIP]
    > 請確認服務正在執行中，否則這個步驟會失敗。 若您已從程式碼變更了基底位址，即應在此步驟中使用修改後的基底位址。

5. 按兩下 [**我的服務專案**] 節點底下的 [ **SayHello** ]。 在**要求**清單的 [**值**] 欄位中輸入您的名稱，**然後按一下 [** 叫用]。

   回復訊息會出現在**回應**清單中。

## <a name="example"></a>範例

下列範例會建立 <xref:System.ServiceModel.ServiceHost> 物件來裝載型別為 `HelloWorldService` 的服務，然後呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 上的 <xref:System.ServiceModel.ServiceHost> 方法。 基底位址由程式碼提供、中繼資料發行已啟用，而且將使用預設端點。

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a>另請參閱

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [How to: Host a WCF Service in IIS](./feature-details/how-to-host-a-wcf-service-in-iis.md)
- [自我裝載](./samples/self-host.md)
- [裝載服務](hosting-services.md)
- [如何：定義服務合約](how-to-define-a-wcf-service-contract.md)
- [如何：履行服務合約](how-to-implement-a-wcf-contract.md)
- [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [使用繫結設定服務與用戶端](using-bindings-to-configure-services-and-clients.md)
- [系統提供的繫結](system-provided-bindings.md)

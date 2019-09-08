---
title: 開發通道
ms.date: 03/30/2017
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
ms.openlocfilehash: 8d0ecb9ea473b78dfc648a1087ae2261406f2b4f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795784"
---
# <a name="developing-channels"></a>開發通道
若要開發可與 Windows Communication Foundation （WCF）應用層搭配使用的通訊協定或傳輸通道，需要數個步驟。 本主題將說明這些步驟，並指引您前往特定主題以取得詳細資訊。 若要瞭解通道模型以及本主題中所提及的各種類型，請參閱[通道模型總覽](channel-model-overview.md)。 如需完整的傳輸通道範例， [請參閱傳輸：UDP](../samples/transport-udp.md)。  
  
## <a name="the-channel-development-task-list"></a>通道開發工作單位清單  
 建立使用者定義通道的步驟如下： 所有的通道都必須：  
  
1. 決定您的 <xref:System.ServiceModel.Channels.IOutputChannel> 和 <xref:System.ServiceModel.Channels.IInputChannel> 所要支援的通道訊息交換模式 (<xref:System.ServiceModel.Channels.IDuplexChannel>、<xref:System.ServiceModel.Channels.IRequestChannel>、<xref:System.ServiceModel.Channels.IReplyChannel>、<xref:System.ServiceModel.Channels.IChannelFactory> 或 <xref:System.ServiceModel.Channels.IChannelListener>)，以及其是否支援這些介面的工作階段變化。 如需詳細資訊，請參閱[選擇訊息交換模式](choosing-a-message-exchange-pattern.md)。  
  
2. 建立支援您訊息交換模式的通道處理站和接聽項 (<xref:System.ServiceModel.Channels.IChannelFactory> 和 <xref:System.ServiceModel.Channels.IChannelListener>)。 如需開發工廠的詳細資訊[，請參閱用戶端：通道處理站和](client-channel-factories-and-channels.md)通道。 如需開發接聽程式的詳細[資訊，請參閱服務：通道接聽程式和](service-channel-listeners-and-channels.md)通道。  
  
3. 確認是否已將任何的網路特定例外狀況標準化為 <xref:System.TimeoutException?displayProperty=nameWithType> 或適當的 <xref:System.ServiceModel.CommunicationException> 衍生類別。 如需詳細資訊，請參閱[處理例外狀況和錯誤](handling-exceptions-and-faults.md)。  
  
4. 若要啟用應用程式層，請新增會將自訂通道加入到通道堆疊中的 <xref:System.ServiceModel.Channels.BindingElement>。 如需詳細資訊，請參閱[建立 BindingElement](creating-a-bindingelement.md)。  
  
 在啟用更完整的應用程式層支援時，需要下列的額外步驟：  
  
1. 新增繫結元素延伸區段，即可將新的繫結元素公開至組態系統。 如需詳細資訊，請參閱設定[和中繼資料支援](configuration-and-metadata-support.md)。  
  
2. 新增中繼資料延伸，即可將功能傳達給其他端點。 如需詳細資訊，請參閱設定[和中繼資料支援](configuration-and-metadata-support.md)。  
  
3. 新增繫結，此繫結會根據妥善定義的設定檔來預先設定繫結項目的堆疊。 如需詳細資訊，請參閱[建立使用者定義的](creating-user-defined-bindings.md)系結。  
  
4. 新增繫結區段和繫結組態項目，即可將繫結公開至組態系統。 如需詳細資訊，請參閱設定[和中繼資料支援](configuration-and-metadata-support.md)。  
  
## <a name="see-also"></a>另請參閱

- [擴充繫結](extending-bindings.md)

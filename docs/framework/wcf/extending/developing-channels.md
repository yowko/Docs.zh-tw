---
title: 開發通道
ms.date: 03/30/2017
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
ms.openlocfilehash: def60ec0cce8da71e7e2d98ff456420949360aed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487421"
---
# <a name="developing-channels"></a>開發通道
若要開發通訊協定和傳輸通道，可與 Windows Communication Foundation (WCF) 應用程式層會需要幾個步驟。 本主題將說明這些步驟，並指引您前往特定主題以取得詳細資訊。 若要了解通道模型和本主題所述的各種類型，請參閱[通道模型概觀](../../../../docs/framework/wcf/extending/channel-model-overview.md)。 如需完成的傳輸通道範例中，請參閱[傳輸： UDP](../../../../docs/framework/wcf/samples/transport-udp.md)。  
  
## <a name="the-channel-development-task-list"></a>通道開發工作單位清單  
 建立使用者定義通道的步驟如下： 所有的通道都必須：  
  
1.  決定您的 <xref:System.ServiceModel.Channels.IOutputChannel> 和 <xref:System.ServiceModel.Channels.IInputChannel> 所要支援的通道訊息交換模式 (<xref:System.ServiceModel.Channels.IDuplexChannel>、<xref:System.ServiceModel.Channels.IRequestChannel>、<xref:System.ServiceModel.Channels.IReplyChannel>、<xref:System.ServiceModel.Channels.IChannelFactory> 或 <xref:System.ServiceModel.Channels.IChannelListener>)，以及其是否支援這些介面的工作階段變化。 如需詳細資訊，請參閱[選擇訊息交換模式](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md)。  
  
2.  建立支援您訊息交換模式的通道處理站和接聽項 (<xref:System.ServiceModel.Channels.IChannelFactory> 和 <xref:System.ServiceModel.Channels.IChannelListener>)。 如需有關開發處理站的詳細資訊，請參閱[用戶端： 通道處理站和通道](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md)。 如需有關開發接聽程式的詳細資訊，請參閱[服務： 通道接聽程式和通道](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md)。  
  
3.  確認是否已將任何的網路特定例外狀況標準化為 <xref:System.TimeoutException?displayProperty=nameWithType> 或適當的 <xref:System.ServiceModel.CommunicationException> 衍生類別。 如需詳細資訊，請參閱[處理的例外狀況和錯誤](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)。  
  
4.  若要啟用應用程式層，請新增會將自訂通道加入到通道堆疊中的 <xref:System.ServiceModel.Channels.BindingElement>。 如需詳細資訊，請參閱[建立 BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)。  
  
 在啟用更完整的應用程式層支援時，需要下列的額外步驟：  
  
1.  新增繫結元素延伸區段，即可將新的繫結元素公開至組態系統。 如需詳細資訊，請參閱[組態與中繼資料支援](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)。  
  
2.  新增中繼資料延伸，即可將功能傳達給其他端點。 如需詳細資訊，請參閱[組態與中繼資料支援](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)。  
  
3.  新增繫結，此繫結會根據妥善定義的設定檔來預先設定繫結項目的堆疊。 如需詳細資訊，請參閱[Creating User-Defined 繫結](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)。  
  
4.  新增繫結區段和繫結組態項目，即可將繫結公開至組態系統。 如需詳細資訊，請參閱[組態與中繼資料支援](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)。  
  
## <a name="see-also"></a>另請參閱  
 [擴充繫結](../../../../docs/framework/wcf/extending/extending-bindings.md)

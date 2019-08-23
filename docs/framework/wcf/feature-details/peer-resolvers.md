---
title: 對等解析程式
ms.date: 03/30/2017
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
ms.openlocfilehash: 0547bb37b03235c61f43cec365551438f7931ad1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909918"
---
# <a name="peer-resolvers"></a>對等解析程式
為了連線至網狀結構，對等節點會需要其他節點的 IP 位址。 IP 位址是透過連絡解析程式服務取得，解析程式服務會取得網狀結構識別碼，並傳回其中位址會對應至以該特定網狀結構識別碼登錄之節點的位址清單。 解析程式會保留已登錄位址的清單，而透過服務登錄網狀結構中的每個節點就可建立此清單。  
  
 您可以透過 `Resolver` 的 <xref:System.ServiceModel.NetPeerTcpBinding> 屬性，指定要使用的 PeerResolver 服務。  
  
## <a name="supported-peer-resolvers"></a>支援的對等解析程式  
 對等通道支援兩種類型的解析程式:對等名稱解析通訊協定 (PNRP) 和自訂解析程式服務。  
  
 根據預設，對等通道會使用 PNRP 對等解析程式服務探索網狀結構中的對等和鄰接項目。 針對無法使用或不可行的情況, Windows Communication Foundation (WCF) 提供替代的伺服器探索服務<xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>, 也就是。 您也可以透過撰寫實作 <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> 介面的類別，明確定義自訂的解析程式服務。  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>對等名稱解析通訊協定 (PNRP)  
 PNRP 是 [!INCLUDE[wv](../../../../includes/wv-md.md)] 的預設解析程式，這是一種分散式的無伺服器名稱解析程式服務。 只要安裝進階網路套件，也可以在 [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] 上使用 PNRP。 如果執行相同版本 PNRP 的兩個用戶端符合特定條件 (例如沒有中介的公司防火牆)，就可以使用此通訊協定找到彼此。 請注意，[!INCLUDE[wv](../../../../includes/wv-md.md)] 隨附的 PNRP 版本比進階網路套件中的版本還新。 請檢查 Microsoft 下載中心，以取得適用於 [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] 的 PNRP 升級。  
  
### <a name="custom-resolver-services"></a>自訂解析程式服務  
 當 PNRP 服務無法使用，或您想要完整控制網狀結構成型時，您可以使用自訂的伺服器解析程式服務。 您可以透過撰寫實作 <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> 介面的解析程式類別，或是使用產品所提供的預設實作 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>，明確定義這項服務。  
  
 根據服務的預設實作，如果用戶端沒有明確重新整理登錄，用戶端登錄會在特定的時間量之後到期。 使用解析程式服務的用戶端必須注意用戶端伺服器延遲時間的上限，才能順利即時重新整理登錄。 這牽涉到在解析程式服務上選擇適當的重新整理逾時值 (`RefreshInterval`)。 (如需詳細資訊, [請參閱 custompeerresolverservice 內部內部:用戶端](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)註冊)。  
  
 應用程式撰寫者也必須考慮如何保障用戶端和自訂解析程式服務之間的連線安全。 在用戶端用來連絡解析程式服務的 <xref:System.ServiceModel.NetTcpBinding> 上使用安全性設定，即可保障連線的安全。 您必須在用於建立對等通道的 `ChannelFactory` 上指定認證 (若使用的話)。 這些認證會傳遞至用來建立自訂解析程式之通道的 `ChannelFactory`。  
  
> [!NOTE]
> 使用本機和即席網路搭配自訂解析程式時，強烈建議使用或支援連結-本機或即席網路的應用程式要包含一種邏輯，這個邏輯會在連線時選取要使用的單一連結-本機位址。 這樣可防止具有多個連結-本機位址的電腦所可能導致的混淆。 為了與此作業保持一致，對等通道每次只會支援使用單一的連結-本機位址。 您可以使用 `ListenIpAddress` 上的 <xref:System.ServiceModel.NetPeerTcpBinding> 屬性來指定這個位址。  
  
 如需如何執行自訂解析程式的示範, 請參閱[對等通道自訂對等解析程式](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90))。  
  
## <a name="in-this-section"></a>本節內容  
 [在 Custompeerresolverservice 內部內:用戶端註冊](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>另請參閱

- [對等通道概念](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
- [對等通道安全性](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [建置對等通道應用程式](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)

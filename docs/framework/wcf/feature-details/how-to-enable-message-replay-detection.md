---
title: HOW TO：啟用訊息重新執行偵測
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
ms.openlocfilehash: df56d3f2bfe351c38ca2e64539de13e4cc556d2a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732338"
---
# <a name="how-to-enable-message-replay-detection"></a>HOW TO：啟用訊息重新執行偵測
當攻擊者複製兩方之間的訊息資料流，並且對其中一方或多方重新執行資料流時，即表示發生重新執行攻擊。 除非緩解攻擊，否則受到攻擊的電腦會將資料流當成合法訊息來處理，導致發生一連串負面的影響，例如項目的重複排序。  
  
 如需有關訊息重新執行偵測的詳細資訊，請參閱[訊息重新執行偵測](https://go.microsoft.com/fwlink/?LinkId=88536)。  
  
 下列程序示範您可以使用來控制使用 Windows Communication Foundation (WCF) 的重新執行偵測的各種屬性。  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>若要透過程式碼在用戶端上控制重新執行偵測  
  
1.  建立用於 <xref:System.ServiceModel.Channels.SecurityBindingElement> 的 <xref:System.ServiceModel.Channels.CustomBinding>。 如需詳細資訊，請參閱 <<c0> [ 如何： 建立自訂繫結使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)。 下列範例會使用 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> (使用 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> 類別的 <xref:System.ServiceModel.Channels.SecurityBindingElement> 來建立)。  
  
2.  請使用 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> 屬性將參照傳回 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> 類別，並在必要時設定下列任何一個屬性：  
  
    1.  `DetectReplay`. 布林值 (Boolean)。 它將控制用戶端是否應該偵測來自伺服器的重新執行。 預設為 `true`。  
  
    2.  `MaxClockSkew`. <xref:System.TimeSpan> 值。 控制在用戶端與伺服器之間重新執行機制可容許的時間誤差。 安全性機制會檢查傳送的時間戳記並判斷它是否已經傳送出去太久了。 預設值是 5 分鐘。  
  
    3.  `ReplayWindow`. `TimeSpan` 值。 它會控制訊息在經由伺服器傳送出去 (透過媒介) 並在抵達用戶端之前，可以在網路中存留的時間長短。 用戶端會追蹤於最近 `ReplayWindow` 傳送的訊息簽章，以利進行重新執行偵測。  
  
    4.  `ReplayCacheSize`. 整數值。 用戶端會將訊息簽章儲存到快取中。 這項設定將指定快取可以儲存的簽章數量。 如果最近一次重新執行視窗中傳送的訊息數量到達快取上限，則會等到最早的快取簽章抵達時間限制才會開始接受新的訊息。 預設值為 500000。  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>若要透過程式碼在服務上控制重新執行偵測  
  
1.  建立用於 <xref:System.ServiceModel.Channels.SecurityBindingElement> 的 <xref:System.ServiceModel.Channels.CustomBinding>。  
  
2.  請使用 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> 屬性將參照傳回 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> 類別，然後如先前所述設定屬性。  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>若要透過組態來控制用戶端或服務的重新執行偵測  
  
1.  建立[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)。  
  
2.  建立 `<security>` 項目。  
  
3.  建立[ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)或是[ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)。  
  
4.  必要時設定 `detectReplays`、`maxClockSkew`、`replayWindow`，和 `replayCacheSize` 的屬性值。 下列範例將同時設定 `<localServiceSettings>`和`<localClientSettings>` 項目的屬性。  
  
    ```xml  
    <customBinding>  
      <binding name="NewBinding0">  
       <textMessageEncoding />  
        <security>  
         <localClientSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
         <localServiceSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
        <secureConversationBootstrap />  
       </security>  
      <httpTransport />  
     </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a>範例  
 下列範例將使用 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 方法來建立 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A>，並設定繫結的重新執行屬性。  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>重新執行範圍：僅限訊息安全性  
 請注意，下列程序僅適用訊息安全性模式。 在 [傳輸] 與 [使用訊息認證的傳輸] 模式中，傳輸機制會偵測重新執行。  
  
## <a name="secure-conversation-notes"></a>安全對話提示  
 針對可啟用安全對話的繫結，您可以同時對應用程式通道，以及安全對話啟動安裝繫結調整這些設定。 例如，您可以關閉應用程式通道的重新執行，但卻針對可建立安全對話的啟動安裝繫結加以啟用。  
  
 如果您並未使用安全對話工作階段，重新執行偵測將無法保證在伺服器陣列案例以及處理序回收期間偵測重新執行。 此情況適用下列系統提供的繫結：  
  
-   <xref:System.ServiceModel.BasicHttpBinding>.  
  
-   <xref:System.ServiceModel.WSHttpBinding>，<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> 屬性設定為 `false`。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   要編譯程式碼時，必須有下列命名空間：  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [安全對話與安全工作階段](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)  
 [\<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)  
 [如何：使用 SecurityBindingElement 建立自訂繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)

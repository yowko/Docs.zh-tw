---
title: "HOW TO：使用 SecurityBindingElement 建立自訂繫結 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "安全性 [WCF]，建立自訂繫結"
ms.assetid: 203a9f9e-3a73-427c-87aa-721c56265b29
caps.latest.revision: 19
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 19
---
# HOW TO：使用 SecurityBindingElement 建立自訂繫結
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 包括數個系統提供之繫結，您可以對這些繫結進行設定，但是自訂這些繫結並不具有設定所有安全性選項時 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所支援的完整彈性。 本主題示範如何直接從個別的繫結元素建立自訂繫結，並強調一些可在建立這類繫結時指定的安全設定。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]建立自訂繫結，請參閱[擴充繫結](../../../../docs/framework/wcf/extending/extending-bindings.md)。  
  
> [!WARNING]
>  <xref:System.ServiceModel.Channels.SecurityBindingElement>不支援<xref:System.ServiceModel.Channels.IDuplexSessionChannel>通道圖案，也就是使用的預設通道圖案 tcp 傳輸時<xref:System.ServiceModel.TransferMode>設為<xref:System.ServiceModel.TransferMode.Buffered>。 您必須設定<xref:System.ServiceModel.TransferMode>至<xref:System.ServiceModel.TransferMode.Streamed>才能使用<xref:System.ServiceModel.Channels.SecurityBindingElement>在此案例中。  
  
## <a name="creating-a-custom-binding"></a>建立自訂繫結  
 在[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]所有繫結所組成*繫結項目*。 每個繫結項目衍生自<xref:System.ServiceModel.Channels.BindingElement>類別。 如果是標準系統提供的繫結，雖然您可以自訂某些屬性設定，但是系統仍會為您先建立並且設定好繫結項目。  
  
 相反地，若要建立自訂繫結，繫結項目所建立及設定和<xref:System.ServiceModel.Channels.CustomBinding>建立從繫結項目。  
  
 若要這樣做，個別的繫結項目加入集合的執行個體所代表<xref:System.ServiceModel.Channels.BindingElementCollection>類別，然後再設定`Elements`屬性`CustomBinding`等同於該物件。 必須按照下列順序加入繫結項目：Transaction Flow、Reliable Session、Security、Composite Duplex、One-way、Stream Security、Message Encoding 然後是 Transport。 請注意，並非每個繫結都需要所列的所有繫結項目。  
  
## <a name="securitybindingelement"></a>SecurityBindingElement  
 三個繫結項目與訊息層級安全性，其中都衍生自<xref:System.ServiceModel.Channels.SecurityBindingElement>類別。 三種<xref:System.ServiceModel.Channels.TransportSecurityBindingElement>， <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>，和<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>。 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>用於提供混合的模式安全性。 當訊息層提供安全性時，則使用另外兩個項目。  
  
 當傳輸層提供安全性時，會使用其他的類別：  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
## <a name="required-binding-elements"></a>必要的繫結項目  
 有很多可能的繫結項目可以與任一繫結進行結合。 但是並非所有的組合都有效。 本節會說明安全性繫結中必須要有的項目。  
  
 有效的安全性繫結會因為許多因素而異，包括：  
  
-   安全性模式。  
  
-   傳輸通訊協定。  
  
-   合約中指定的訊息交換模式 (MEP)。  
  
 下表針對前述的因素，列出每一個組合的有效繫結項目堆疊組態。 請注意，這些都是基本需求。 您可以將其他繫結項目加入繫結中，如訊息編碼繫結項目、交易繫結項目以及其他繫結項目。  
  
|安全性模式|Transport|合約訊息交換模式|合約訊息交換模式|合約訊息交換模式|  
|-------------------|---------------|---------------------------------------|---------------------------------------|---------------------------------------|  
|||`Datagram`|`Request Reply`|`Duplex`|  
|Transport|Https||||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP||||  
|||OneWayBindingElement|||  
|||SSL 或 Windows StreamSecurityBindingElement|SSL 或 Windows StreamSecurityBindingElement|SSL 或 Windows StreamSecurityBindingElement|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|訊息|Http|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement (驗證模式 = SecureConversation)|  
|||||CompositeDuplexBindingElement|  
|||OneWayBindingElement||OneWayBindingElement|  
|||HttpTransportBindingElement|HttpTransportBindingElement|HttpTransportBindingElement|  
||Tcp|SecurityBindingElement|SecurityBindingElement|SymmetricSecurityBindingElement (驗證模式 = SecureConversation)|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|混合式 (使用訊息認證的傳輸)|Https|TransportSecurityBindingElement|TransportSecurityBindingElement||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP|TransportSecurityBindingElement|SymmetricSecurityBindingElement (驗證模式 = SecureConversation)|SymmetricSecurityBindingElement (驗證模式 = SecureConversation)|  
|||OneWayBindingElement|||  
|||SSL 或 Windows StreamSecurityBindingElement|SSL 或 Windows StreamSecurityBindingElement|SSL 或 Windows StreamSecurityBindingElement|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
  
 請注意，SecurityBindingElements 有許多可以設定的項目。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][SecurityBindingElement 驗證模式](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][安全對話與安全工作階段](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-create-a-custom-binding-that-uses-a-symmetricsecuritybindingelement"></a>若要建立使用 SymmetricSecurityBindingElement 的自訂繫結  
  
1.  建立的執行個體<xref:System.ServiceModel.Channels.BindingElementCollection>類別名稱`outputBec`。  
  
2.  呼叫靜態方法`M:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement(true)`，它會傳回的執行個體<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>類別。  
  
3.  新增<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>集合 (`outputBec`) 藉由呼叫`Add`方法<xref:System.Collections.ObjectModel.Collection%601>的<xref:System.ServiceModel.Channels.BindingElement>類別。  
  
4.  建立的執行個體<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>類別，並將它加入至集合 (`outputBec`)。 這會指定繫結使用的編碼方式。  
  
5.  建立<xref:System.ServiceModel.Channels.HttpTransportBindingElement>並將它加入至集合 (`outputBec`)。 這會指定繫結要使用 HTTP 傳輸。  
  
6.  建立新的自訂繫結所建立的執行個體<xref:System.ServiceModel.Channels.CustomBinding>類別，且傳遞集合`outputBec`建構函式。  
  
7.  產生的自訂繫結共用許多相同的特性標準<xref:System.ServiceModel.WSHttpBinding>。 它會指定訊息層級安全性和 Windows 認證，但停用安全工作階段，並要求指定超出範圍的認證，且不會加密簽章。 最後一個可以控制只是藉由設定<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A>步驟 4 中所示的屬性。 其他兩項可透過使用標準繫結上的設定來控制。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>說明  
 下列範例提供完整的函式來建立使用自訂繫結<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[c_CustomBinding#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#20)]
 [!code-vb[c_CustomBinding#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombinding/vb/source.vb#20)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>   
 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>   
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [擴充繫結](../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [系統提供繫結](../../../../docs/framework/wcf/system-provided-bindings.md)
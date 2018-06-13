---
title: HOW TO：使用 SecurityBindingElement 建立自訂繫結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating custom bindings
ms.assetid: 203a9f9e-3a73-427c-87aa-721c56265b29
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1e288daeb717fa9fa041d552cac4ec5d0cd28808
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495628"
---
# <a name="how-to-create-a-custom-binding-using-the-securitybindingelement"></a>HOW TO：使用 SecurityBindingElement 建立自訂繫結
Windows Communication Foundation (WCF) 包含數種系統提供繫結，您可以設定，但不是會提供完整的彈性設定 WCF 支援的所有安全性選項時。 本主題示範如何直接從個別的繫結元素建立自訂繫結，並強調一些可在建立這類繫結時指定的安全設定。 如需有關如何建立自訂繫結的詳細資訊，請參閱[擴充繫結](../../../../docs/framework/wcf/extending/extending-bindings.md)。  
  
> [!WARNING]
>  <xref:System.ServiceModel.Channels.SecurityBindingElement> 不支援 <xref:System.ServiceModel.Channels.IDuplexSessionChannel> 通道圖案，當 <xref:System.ServiceModel.TransferMode> 設定為 <xref:System.ServiceModel.TransferMode.Buffered> 時，這是 TCP 傳輸使用的預設通道圖案。 您必須將 <xref:System.ServiceModel.TransferMode> 設定為 <xref:System.ServiceModel.TransferMode.Streamed>，才能在這個情況中使用 <xref:System.ServiceModel.Channels.SecurityBindingElement>。  
  
## <a name="creating-a-custom-binding"></a>建立自訂繫結  
 在 WCF 中的所有繫結所組成*繫結項目*。 每個繫結項目均衍生自 <xref:System.ServiceModel.Channels.BindingElement> 類別。 如果是標準系統提供的繫結，雖然您可以自訂某些屬性設定，但是系統仍會為您先建立並且設定好繫結項目。  
  
 相反的，若要建立自訂繫結，會建立並且設定繫結項目，並且從自訂項目建立一個<xref:System.ServiceModel.Channels.CustomBinding>。  
  
 若要進行這個步驟，您可以將個別的繫結項目加入到由 <xref:System.ServiceModel.Channels.BindingElementCollection>`Elements`類別之執行個體所表示的集合，然後，將 `CustomBinding`的 屬性設定為等同於該物件的項目。 必須按照下列順序加入繫結項目：Transaction Flow、Reliable Session、Security、Composite Duplex、One-way、Stream Security、Message Encoding 然後是 Transport。 請注意，並非每個繫結都需要所列的所有繫結項目。  
  
## <a name="securitybindingelement"></a>SecurityBindingElement  
 有三個繫結項目與訊息層級安全性相關，這些項目全都衍生自 <xref:System.ServiceModel.Channels.SecurityBindingElement> 類別。 這三個項目分別是 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 和 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>。 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> 用於提供混合模式安全性。 當訊息層提供安全性時，則使用另外兩個項目。  
  
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
  
 下表針對前述的因素，列出每一個組合的有效繫結項目堆疊組態。 請注意，這些都是基本需求。 您可以將其他繫結程序項目加入繫結程序中，如訊息編碼繫結程序項目、異動繫結程序項目以及其他繫結程序項目。  
  
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
  
 請注意，SecurityBindingElements 有許多可以設定的項目。 如需詳細資訊，請參閱[SecurityBindingElement 驗證模式](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)。  
  
 如需詳細資訊，請參閱[安全對話與安全工作階段](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-create-a-custom-binding-that-uses-a-symmetricsecuritybindingelement"></a>若要建立使用 SymmetricSecurityBindingElement 的自訂繫結  
  
1.  建立名稱為 <xref:System.ServiceModel.Channels.BindingElementCollection> 之 `outputBec` 類別的執行個體。  
  
2.  呼叫靜態方法 `M:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement(true)`，此方法會傳回 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>類別。  
  
3.  將 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 新增至集合 (`outputBec`)，方法是呼叫 `Add` 類別其 <xref:System.Collections.ObjectModel.Collection%601> 的 <xref:System.ServiceModel.Channels.BindingElement> 方法。  
  
4.  建立 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> 類別的執行個體，並將它新增至集合 (`outputBec`)。 這會指定繫結使用的編碼方式。  
  
5.  建立 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>，並將它新增至集合 (`outputBec`)。 這會指定繫結要使用 HTTP 傳輸。  
  
6.  建立新自訂繫結，方式是建立 <xref:System.ServiceModel.Channels.CustomBinding> 類別的執行個體，並將 `outputBec` 集合傳遞至建構函式。  
  
7.  產生的自訂繫結會有許多與標準 <xref:System.ServiceModel.WSHttpBinding> 相同的特性。 它會指定訊息層級安全性和 Windows 認證，但停用安全工作階段，並要求指定超出範圍的認證，且不會加密簽章。 最後一項只能透過依照步驟 4 的方式設定 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A> 屬性來控制，其他兩項可透過使用標準繫結上的設定來控制。 其他兩項可透過使用標準繫結程序上的設定來控制。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例提供完整的函式，可建立使用 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 的自訂繫結。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[c_CustomBinding#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#20)]
 [!code-vb[c_CustomBinding#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombinding/vb/source.vb#20)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [擴充繫結](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [系統提供的繫結](../../../../docs/framework/wcf/system-provided-bindings.md)

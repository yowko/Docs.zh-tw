---
title: 作法：自訂系統提供的繫結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: 6b92382b4a37168c33f9e97077ad292d27ea5bc3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797019"
---
# <a name="how-to-customize-a-system-provided-binding"></a>HOW TO：自訂系統提供的繫結
Windows Communication Foundation （WCF）包含數個系統提供的系結，可讓您設定基礎繫結項目的某些屬性，但不是所有屬性。 本主題示範如何設定繫結項目上的屬性來建立自訂繫結。  
  
 如需如何直接建立和設定繫結項目的詳細資訊，而不使用系統提供的系結，請參閱[自訂](custom-bindings.md)系結。  
  
 如需建立和擴充自訂系結的詳細資訊，請參閱[擴充](extending-bindings.md)系結。  
  
 在 WCF 中，所有系結都是由*綁定*項所組成。 每個繫結項目均衍生自 <xref:System.ServiceModel.Channels.BindingElement> 類別。 諸如 <xref:System.ServiceModel.BasicHttpBinding> 的系統提供繫結，會建立並設定自有的繫結項目。 本主題說明如何存取與變更這些繫結項目的屬性，而這些屬性並未直接在繫結上公開 (特別是 <xref:System.ServiceModel.BasicHttpBinding> 類別)。  
  
 個別的繫結項目會包含在由<xref:System.ServiceModel.Channels.BindingElementCollection>類別表示的集合中，並依此順序新增：交易流程，可靠會話，安全性，複合雙工，單向，資料流程安全性，訊息編碼和傳輸。 請注意，並非每個繫結都需要所列的所有繫結項目。 使用者定義的繫結項目也可以出現在此繫結項目集合中，而且必須依照前述順序。 例如，使用者定義的傳輸必須是繫結項目集合中的最後一個項目。  
  
 <xref:System.ServiceModel.BasicHttpBinding> 類別包含三個繫結項目：  
  
1. 一種選擇性的安全性繫結項目，可以是搭配 HTTP 傳輸 (訊息層級安全性) 一起使用的 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> 類別，或是當傳輸層提供安全性時所使用的 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> 類別 (這時會使用 HTTPS 傳輸)。  
  
2. 必要的訊息編碼器繫結項目，可以是 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> 或 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>。  
  
3. 必要的傳輸繫結項目，可以是 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 或 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>。  
  
 在此範例中，我們會建立系結的實例、從它產生*自訂*系結、檢查自訂系結中的繫結項目，以及當我們找到 HTTP 繫結項目時`KeepAliveEnabled` ，將`false`其屬性設定為。 `KeepAliveEnabled` 屬性不會直接在 `BasicHttpBinding` 上公開，因此我們必須建立自訂繫結以向下巡覽至繫結項目並設定此屬性。  
  
### <a name="to-modify-a-system-provided-binding"></a>若要修改系統提供的繫結  
  
1. 建立 <xref:System.ServiceModel.BasicHttpBinding> 類別的執行個體，並將其安全性模式設為訊息層級。  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2. 從繫結中建立自訂繫結，並從其中一個自訂繫結的屬性中建立 <xref:System.ServiceModel.Channels.BindingElementCollection> 類別。  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3. 對 <xref:System.ServiceModel.Channels.BindingElementCollection> 類別執行迴圈，並在找到 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 類別時，將其 <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> 屬性設為 `false`。  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [自訂繫結](custom-bindings.md)

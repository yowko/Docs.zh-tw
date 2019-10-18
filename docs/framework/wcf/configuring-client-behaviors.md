---
title: 設定用戶端行為
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: ca466af71f62ef72e021753b132afdc847f75d76
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320686"
---
# <a name="configuring-client-behaviors"></a>設定用戶端行為
Windows Communication Foundation （WCF）會以兩種方式設定行為：藉由參考行為設定（定義于用戶端應用程式設定檔的 `<behavior>` 區段中），或以程式設計方式在呼叫應用程式中進行。 這個主題將描述這兩種方法。  
  
 使用組態檔時，行為組態都是具名的組態設定集合。 每個行為組態的名稱必須是獨一無二的。 會在端點組態的 `behaviorConfiguration` 屬性中使用這個字串，以便將端點連結至行為。  
  
## <a name="example"></a>範例  
 下列組態程式碼會定義名稱為 `myBehavior` 的行為。 用戶端端點會參考 `behaviorConfiguration` 屬性中的這個行為。  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="myBehavior">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="myBinding" maxReceivedMessageSize="10000" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="myAddress" binding="basicHttpBinding" bindingConfiguration="myBinding" behaviorConfiguration="myBehavior" contract="myContract" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-behaviors-programmatically"></a>以程式設計方式使用行為  
 您也可以在開啟用戶端之前，先在 Windows Communication Foundation （WCF）用戶端物件或用戶端通道處理站物件上尋找適當的 `Behaviors` 屬性，以程式設計方式設定或插入行為。  
  
## <a name="example"></a>範例  
 下列程式碼範例會示範如何以程式設計的方式插入行為，其方法是先存取傳回自 <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> 屬性之 <xref:System.ServiceModel.Description.ServiceEndpoint> 上的 <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> 屬性，再建立通道物件。  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>請參閱

- [\<behaviors >](../configure-apps/file-schema/wcf/behaviors.md)

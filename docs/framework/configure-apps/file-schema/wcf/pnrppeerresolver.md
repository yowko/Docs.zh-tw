---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: e7e82117304ac133e5e84c0fc36b987560bcef96
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933803"
---
# <a name="pnrppeerresolver"></a>\<pnrpPeerResolver>
指定對等名稱解析通訊協定 (Peer Name Resolution Protocol，PNRP) 解析程式做為解析程式使用。 這是一個選擇性的項目，因為 PNRP 是預設的解析程式。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<系結 >  
\<pnrpResolver>  
  
## <a name="syntax"></a>語法  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|resolverType|字串，指定要使用的解析程式。 這是一個選擇性的屬性。 如果未設定，或如果設定為空字串，則使用 PNRP。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="example"></a>範例  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [繫結](../../../wcf/bindings.md)
- [擴充繫結](../../../wcf/extending/extending-bindings.md)
- [自訂繫結](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [對等解析程式](../../../wcf/feature-details/peer-resolvers.md)

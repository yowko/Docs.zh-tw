---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 0a8cc60226b13552d47faec3a156ed1f59acacb9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181397"
---
# \<pnrpPeerResolver>

指定對等名稱解析通訊協定 (Peer Name Resolution Protocol，PNRP) 解析程式做為解析程式使用。 這是一個選擇性的項目，因為 PNRP 是預設的解析程式。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|resolverType|字串，指定要使用的解析程式。 此屬性是選擇性的。 如果未設定，或如果設定為空字串，則使用 PNRP。|  
  
### <a name="child-elements"></a>子元素  

 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|定義自訂繫結的所有繫結功能。|  
  
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

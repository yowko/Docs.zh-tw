---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: a5209efddd489f8cb04b3266e6ba0bb033eeae6c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176015"
---
# \<compositeDuplex>

定義繫結項目，這是當用戶端必須公開 (Expose) 服務的端點才能將訊息傳回用戶端時所使用的項目。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|clientBaseAddress|URI，設定雙工模式中返回通道的位址。 服務會使用這個位址與用戶端接觸並建立連接。<br /><br /> 如果未設定此屬性， `full qualified name+default port\TemporaryIndigoAddress\guid` 則會產生預設位址 ""。 預設值為 `null`。|  
  
### <a name="child-elements"></a>子元素  

 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="remarks"></a>備註  

 這個組態項目是和本身不允許雙工通訊的傳輸一起使用，例如 HTTP。 相反地，TCP 本身就允許雙工通訊，因此不需要使用這個繫結項目也可讓服務將訊息傳回用戶端。  
  
 用戶端必須公開位址，才能讓服務接觸並建立連接。 這個用戶端位址是由 `clientBaseAddress` 屬性提供。 請注意，如果使用者未明確設定此屬性，則 Windows Communication Foundation (WCF) 會自動產生 ClientBaseAddress。  
  
## <a name="example"></a>範例  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [繫結](../../../wcf/bindings.md)
- [擴充繫結](../../../wcf/extending/extending-bindings.md)
- [自訂繫結](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

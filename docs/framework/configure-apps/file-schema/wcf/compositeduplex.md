---
title: '&lt;compositeDuplex&gt;'
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: e00cc6f3214dc9a040a9b6170271b1f4188d1631
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601619"
---
# <a name="ltcompositeduplexgt"></a>&lt;compositeDuplex&gt;
定義繫結項目，這是當用戶端必須公開 (Expose) 服務的端點才能將訊息傳回用戶端時所使用的項目。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<compositeDuplex>  
  
## <a name="syntax"></a>語法  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|clientBaseAddress|URI，設定雙工模式中返回通道的位址。 服務會使用這個位址與用戶端接觸並建立連接。<br /><br /> 如果這個屬性未設定，預設位址"`full qualified name+default port\TemporaryIndigoAddress\guid`」 產生。 預設為 `null`。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
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
- [繫結](../../../../../docs/framework/wcf/bindings.md)
- [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

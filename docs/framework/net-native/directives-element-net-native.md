---
title: '&lt;Directives&gt; 項目 (.NET Native)'
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 497ec1a432352e3b9f50bd94e03e95e98edcfd55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725635"
---
# <a name="ltdirectivesgt-element-net-native"></a>&lt;Directives&gt; 項目 (.NET Native)
針對.NET 原生的每個執行階段指示詞檔案中的根項目。  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a>語法  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`xmlns`|XML 命名空間。 其值永遠是 **」 http://schemas.microsoft.com/netfx/2013/01/metadata"**。|  
  
## <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|做為容器，以包含整個應用程式中，可將中繼資料用於反映的類型和類型成員。|  
|[\<程式庫>](../../../docs/framework/net-native/library-element-net-native.md)|定義子類型和類型成員會在執行階段需要中繼資料的組件。|  
  
## <a name="remarks"></a>備註  
 每個執行階段指示詞檔案都只能包含一個 `<Directives>` 元素。  
  
 `<Directives>` 項目可以包含零或一個 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 項目，以及零、一或多個 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 項目。  
  
## <a name="see-also"></a>另請參閱
- [執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [執行階段指示詞項目](../../../docs/framework/net-native/runtime-directive-elements.md)

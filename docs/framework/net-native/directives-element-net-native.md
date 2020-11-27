---
title: '<Directives> 元素 ( .NET Native) '
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 524c30872e218f6428491507bbfb4ca54b6061b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251096"
---
# <a name="directives-element-net-native"></a>\<Directives> 元素 ( .NET Native) 

.NET Native 的每個執行時間指示詞檔案中的根項目。  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a>Syntax  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`xmlns`|XML 命名空間。 其值一律為 `http://schemas.microsoft.com/netfx/2013/01/metadata` 。|  
  
## <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|做為容器，以包含整個應用程式中，可將中繼資料用於反映的類型和類型成員。|  
|[\<Library>](library-element-net-native.md)|定義子類型和類型成員會在執行階段需要中繼資料的組件。|  
  
## <a name="remarks"></a>備註  

 每個執行階段指示詞檔案都只能包含一個 `<Directives>` 元素。  
  
 `<Directives>`元素可以包含零個或一個 [\<Application>](application-element-net-native.md) 元素，以及零個、一個或多個 [\<Library>](library-element-net-native.md) 元素。  
  
## <a name="see-also"></a>另請參閱

- [執行階段指示詞 (rd.xml) 組態檔參考](runtime-directives-rd-xml-configuration-file-reference.md)
- [執行階段指示詞項目](runtime-directive-elements.md)

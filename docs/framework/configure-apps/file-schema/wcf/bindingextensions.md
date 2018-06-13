---
title: '&lt;bindingExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: f99b38ede66dbecb44f9e8e67f921943071672ca
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750771"
---
# <a name="ltbindingextensionsgt"></a>&lt;bindingExtensions&gt;
這個區段會啟用電腦或應用程式組態檔中使用者定義繫結的使用。 您可以透過使用 `add` 關鍵字，將項目的 `type` 屬性設定為使用者定義繫結，並將 `name` 屬性設定為使用者定義繫結的名稱，來將使用者定義繫結加入至這個集合。  
  
 繫結延伸可讓使用者建立使用者定義繫結，做為端點組態的一部分。 就程式設計角度而言，繫結延伸是實作抽象類別 (Abstract Class) <xref:System.ServiceModel.Channels.Binding> 的型別。  
  
 下列範例使用 `add` 項目，以及 `name` 屬性，將繫結延伸加入至組態檔的 `bindingElementExtensions` 區段中。  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <bindingExtensions>  
           <add name="MyBinding" type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </bindingExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 若要將組態功能加入至項目，使用者必須寫入並註冊 `bindingSection` 項目。 如需這方面的詳細資訊，請參閱 <xref:System.Configuration>。  
  
 在定義項目及其組態型別後，延伸即可做為端點的一部分，如下列範例所示。  
  
```xml  
<services>  
    <service name="MyService">  
        <endpoint address="myAddress" binding="MyBinding" />  
    </service>  
</services>  
```  
  
## <a name="see-also"></a>另請參閱  
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)

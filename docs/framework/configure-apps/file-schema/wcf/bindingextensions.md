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
# <a name="ltbindingextensionsgt"></a><span data-ttu-id="d3cfc-102">&lt;bindingExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="d3cfc-102">&lt;bindingExtensions&gt;</span></span>
<span data-ttu-id="d3cfc-103">這個區段會啟用電腦或應用程式組態檔中使用者定義繫結的使用。</span><span class="sxs-lookup"><span data-stu-id="d3cfc-103">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="d3cfc-104">您可以透過使用 `add` 關鍵字，將項目的 `type` 屬性設定為使用者定義繫結，並將 `name` 屬性設定為使用者定義繫結的名稱，來將使用者定義繫結加入至這個集合。</span><span class="sxs-lookup"><span data-stu-id="d3cfc-104">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>  
  
 <span data-ttu-id="d3cfc-105">繫結延伸可讓使用者建立使用者定義繫結，做為端點組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="d3cfc-105">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="d3cfc-106">就程式設計角度而言，繫結延伸是實作抽象類別 (Abstract Class) <xref:System.ServiceModel.Channels.Binding> 的型別。</span><span class="sxs-lookup"><span data-stu-id="d3cfc-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>  
  
 <span data-ttu-id="d3cfc-107">下列範例使用 `add` 項目，以及 `name` 屬性，將繫結延伸加入至組態檔的 `bindingElementExtensions` 區段中。</span><span class="sxs-lookup"><span data-stu-id="d3cfc-107">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="d3cfc-108">若要將組態功能加入至項目，使用者必須寫入並註冊 `bindingSection` 項目。</span><span class="sxs-lookup"><span data-stu-id="d3cfc-108">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="d3cfc-109">如需這方面的詳細資訊，請參閱 <xref:System.Configuration>。</span><span class="sxs-lookup"><span data-stu-id="d3cfc-109">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="d3cfc-110">在定義項目及其組態型別後，延伸即可做為端點的一部分，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d3cfc-110">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example.</span></span>  
  
```xml  
<services>  
    <service name="MyService">  
        <endpoint address="myAddress" binding="MyBinding" />  
    </service>  
</services>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3cfc-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3cfc-111">See Also</span></span>  
 [<span data-ttu-id="d3cfc-112">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="d3cfc-112">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)

---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: bd6aeb32e0994bceb9e56bcb1c6267f4cb64a5a4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73039150"
---
# \<bindingExtensions>

<span data-ttu-id="98f55-101">這個區段會啟用電腦或應用程式組態檔中使用者定義繫結的使用。</span><span class="sxs-lookup"><span data-stu-id="98f55-101">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="98f55-102">您可以透過使用 `add` 關鍵字，將項目的 `type` 屬性設定為使用者定義繫結，並將 `name` 屬性設定為使用者定義繫結的名稱，來將使用者定義繫結加入至這個集合。</span><span class="sxs-lookup"><span data-stu-id="98f55-102">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>

<span data-ttu-id="98f55-103">繫結延伸可讓使用者建立使用者定義繫結，做為端點組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="98f55-103">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="98f55-104">就程式設計角度而言，繫結延伸是實作抽象類別 (Abstract Class) <xref:System.ServiceModel.Channels.Binding> 的型別。</span><span class="sxs-lookup"><span data-stu-id="98f55-104">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>

<span data-ttu-id="98f55-105">下列範例會使用專案 `add` ，以及屬性，將系結 `name` 延伸模組新增至 `bindingExtensions` 設定檔的區段：</span><span class="sxs-lookup"><span data-stu-id="98f55-105">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingExtensions` section of the configuration file:</span></span>

```xml
<system.serviceModel>
  <extensions>
    <bindingExtensions>
      <add name="MyBinding"
           type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingExtensions>
  </extensions>
</system.serviceModel>
```

<span data-ttu-id="98f55-106">若要將組態功能加入至項目，使用者必須寫入並註冊 `bindingSection` 項目。</span><span class="sxs-lookup"><span data-stu-id="98f55-106">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="98f55-107">如需這方面的詳細資訊，請參閱 <xref:System.Configuration>。</span><span class="sxs-lookup"><span data-stu-id="98f55-107">For more information on this, see the <xref:System.Configuration> documentation.</span></span>

<span data-ttu-id="98f55-108">定義專案及其設定型別之後，擴充功能可以當做端點的一部分使用，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="98f55-108">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example:</span></span>

```xml
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```

## <a name="see-also"></a><span data-ttu-id="98f55-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98f55-109">See also</span></span>

- [<span data-ttu-id="98f55-110">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="98f55-110">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)

---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: a4bbd677aba27d93389f8d2f99aadd801c86b65f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172836"
---
# \<userDefinedType>

<span data-ttu-id="14e12-101">表示要包含在服務合約中的使用者定義型別 (User Defined Type，UDT)。</span><span class="sxs-lookup"><span data-stu-id="14e12-101">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<userDefinedTypes>**](userdefinedtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userDefinedType>**  
  
## <a name="syntax"></a><span data-ttu-id="14e12-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="14e12-102">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14e12-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="14e12-103">Attributes and Elements</span></span>  

 <span data-ttu-id="14e12-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="14e12-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14e12-105">屬性</span><span class="sxs-lookup"><span data-stu-id="14e12-105">Attributes</span></span>  
  
|<span data-ttu-id="14e12-106">屬性</span><span class="sxs-lookup"><span data-stu-id="14e12-106">Attribute</span></span>|<span data-ttu-id="14e12-107">描述</span><span class="sxs-lookup"><span data-stu-id="14e12-107">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="14e12-108">選擇性屬性，其中包含提供可讀型別名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="14e12-108">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="14e12-109">雖然這不是供執行階段使用，但是可幫助讀者分辨型別。</span><span class="sxs-lookup"><span data-stu-id="14e12-109">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="14e12-110">GUID 字串，識別已註冊型別程式庫內的特定 UDT 型別。</span><span class="sxs-lookup"><span data-stu-id="14e12-110">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="14e12-111">GUID 字串，識別定義此型別的已註冊型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="14e12-111">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="14e12-112">字串，識別定義此型別的型別程式庫版本。</span><span class="sxs-lookup"><span data-stu-id="14e12-112">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14e12-113">子元素</span><span class="sxs-lookup"><span data-stu-id="14e12-113">Child Elements</span></span>  

 <span data-ttu-id="14e12-114">無。</span><span class="sxs-lookup"><span data-stu-id="14e12-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14e12-115">父項目</span><span class="sxs-lookup"><span data-stu-id="14e12-115">Parent Elements</span></span>  
  
|<span data-ttu-id="14e12-116">項目</span><span class="sxs-lookup"><span data-stu-id="14e12-116">Element</span></span>|<span data-ttu-id="14e12-117">描述</span><span class="sxs-lookup"><span data-stu-id="14e12-117">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="14e12-118">`userDefinedType` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="14e12-118">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14e12-119">備註</span><span class="sxs-lookup"><span data-stu-id="14e12-119">Remarks</span></span>  

 <span data-ttu-id="14e12-120">COM+ 整合執行階段會藉由檢查型別程式庫來建立服務。</span><span class="sxs-lookup"><span data-stu-id="14e12-120">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="14e12-121">當 COM+ 元件包含傳遞 VARIANT 的方法時，系統便無法在執行階段之前判斷要傳遞的實際型別。</span><span class="sxs-lookup"><span data-stu-id="14e12-121">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="14e12-122">因此，嘗試在 VARIANT 內傳遞使用者定義型別 (UDT) 會因為該型別不是序列化的已知型別而失敗。</span><span class="sxs-lookup"><span data-stu-id="14e12-122">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="14e12-123">如果要避免這個問題，您可以將這些 UDT 新增至組態檔中，以便包含它們做為適當服務合約中的已知型別。</span><span class="sxs-lookup"><span data-stu-id="14e12-123">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="14e12-124">如果要這樣做，您必須唯一識別這些 UDT 和合約，也就是使用其原始的 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="14e12-124">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="14e12-125">下列範例將示範如何將兩個特定的 UDT 新增至組態檔的 <`userDefinedTypes`> 區段，以達成這個目的。</span><span class="sxs-lookup"><span data-stu-id="14e12-125">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <userDefinedTypes>
      <userDefinedType name="CustomerType"
                       typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"
                       typeLibVersion="1.0"
                       typeDefID="{D129765C-F211-434e-825A-9A63198C41F2}">
      </userDefinedType>
      <userDefinedType name="AddressType"
                       typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"
                       typeLibVersion="1.0"
                       typeDefID="{4616AE0D-687A-43B7-BC63-141AE3DFD099}">
      </userDefinedType>
    </userDefinedTypes>
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="14e12-126">當初始化服務時，整合執行階段會查詢指定的型別，並將它們加入做為指定合約的已知型別集合。</span><span class="sxs-lookup"><span data-stu-id="14e12-126">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14e12-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14e12-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="14e12-128">與 COM + 應用程式整合</span><span class="sxs-lookup"><span data-stu-id="14e12-128">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="14e12-129">作法：設定 COM+ 服務設定</span><span class="sxs-lookup"><span data-stu-id="14e12-129">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)

---
title: '&lt;userDefinedType&gt;'
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: ffa9480312c278097ae110c686fb507209c117e1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755275"
---
# <a name="ltuserdefinedtypegt"></a><span data-ttu-id="18126-102">&lt;userDefinedType&gt;</span><span class="sxs-lookup"><span data-stu-id="18126-102">&lt;userDefinedType&gt;</span></span>
<span data-ttu-id="18126-103">表示要包含在服務合約中的使用者定義型別 (User Defined Type，UDT)。</span><span class="sxs-lookup"><span data-stu-id="18126-103">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
 <span data-ttu-id="18126-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="18126-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="18126-105">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="18126-105">\<comContracts></span></span>  
<span data-ttu-id="18126-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="18126-106">\<comContract></span></span>  
<span data-ttu-id="18126-107">\<userDefinedTypes ></span><span class="sxs-lookup"><span data-stu-id="18126-107">\<userDefinedTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18126-108">語法</span><span class="sxs-lookup"><span data-stu-id="18126-108">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18126-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="18126-109">Attributes and Elements</span></span>  
 <span data-ttu-id="18126-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="18126-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18126-111">屬性</span><span class="sxs-lookup"><span data-stu-id="18126-111">Attributes</span></span>  
  
|<span data-ttu-id="18126-112">屬性</span><span class="sxs-lookup"><span data-stu-id="18126-112">Attribute</span></span>|<span data-ttu-id="18126-113">描述</span><span class="sxs-lookup"><span data-stu-id="18126-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="18126-114">選擇性屬性，其中包含提供可讀型別名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="18126-114">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="18126-115">雖然這不是供執行階段使用，但是可幫助讀者分辨型別。</span><span class="sxs-lookup"><span data-stu-id="18126-115">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="18126-116">GUID 字串，識別已註冊型別程式庫內的特定 UDT 型別。</span><span class="sxs-lookup"><span data-stu-id="18126-116">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="18126-117">GUID 字串，識別定義此型別的已註冊型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="18126-117">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="18126-118">字串，識別定義此型別的型別程式庫版本。</span><span class="sxs-lookup"><span data-stu-id="18126-118">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18126-119">子項目</span><span class="sxs-lookup"><span data-stu-id="18126-119">Child Elements</span></span>  
 <span data-ttu-id="18126-120">無。</span><span class="sxs-lookup"><span data-stu-id="18126-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18126-121">父項目</span><span class="sxs-lookup"><span data-stu-id="18126-121">Parent Elements</span></span>  
  
|<span data-ttu-id="18126-122">項目</span><span class="sxs-lookup"><span data-stu-id="18126-122">Element</span></span>|<span data-ttu-id="18126-123">描述</span><span class="sxs-lookup"><span data-stu-id="18126-123">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="18126-124">`userDefinedType` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="18126-124">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18126-125">備註</span><span class="sxs-lookup"><span data-stu-id="18126-125">Remarks</span></span>  
 <span data-ttu-id="18126-126">COM+ 整合執行階段會藉由檢查型別程式庫來建立服務。</span><span class="sxs-lookup"><span data-stu-id="18126-126">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="18126-127">當 COM+ 元件包含傳遞 VARIANT 的方法時，系統便無法在執行階段之前判斷要傳遞的實際型別。</span><span class="sxs-lookup"><span data-stu-id="18126-127">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="18126-128">因此，嘗試在 VARIANT 內傳遞使用者定義型別 (UDT) 會因為該型別不是序列化的已知型別而失敗。</span><span class="sxs-lookup"><span data-stu-id="18126-128">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="18126-129">如果要避免這個問題，您可以將這些 UDT 新增至組態檔中，以便包含它們做為適當服務合約中的已知型別。</span><span class="sxs-lookup"><span data-stu-id="18126-129">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="18126-130">如果要這樣做，您必須唯一識別這些 UDT 和合約，也就是使用其原始的 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="18126-130">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="18126-131">下列範例將示範如何將兩個特定的 UDT 新增至組態檔的 <`userDefinedTypes`> 區段，以達成這個目的。</span><span class="sxs-lookup"><span data-stu-id="18126-131">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
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
  
 <span data-ttu-id="18126-132">當初始化服務時，整合執行階段會查詢指定的型別，並將它們加入做為指定合約的已知型別集合。</span><span class="sxs-lookup"><span data-stu-id="18126-132">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18126-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18126-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>  
 <xref:System.ServiceModel.Configuration.ComUdtElementCollection>  
 <xref:System.ServiceModel.Configuration.ComUdtElement>  
 [<span data-ttu-id="18126-134">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="18126-134">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="18126-135">整合 COM 應用程式</span><span class="sxs-lookup"><span data-stu-id="18126-135">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="18126-136">如何：設定 COM+ 服務設定</span><span class="sxs-lookup"><span data-stu-id="18126-136">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)

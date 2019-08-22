---
title: authenticationModules 的 <add> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/add
helpviewer_keywords:
- authenticationModules, add element
- add element, authenticationModules
- <authenticationModules>, add element
- <add> element, authenticationModules
ms.assetid: 333c5fb0-a2ab-4db8-8531-a7fe37bb9b5b
ms.openlocfilehash: d72371921a85ff5a68dd9017f0fe8cf5d28557dd
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664242"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="cc4c0-102">\<新增 Authenticationmodules 專案的 > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="cc4c0-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="cc4c0-103">將驗證模組新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="cc4c0-103">Adds an authentication module to the application.</span></span>  
  
 <span data-ttu-id="cc4c0-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="cc4c0-104">\<configuration></span></span>  
<span data-ttu-id="cc4c0-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="cc4c0-105">\<system.net></span></span>  
<span data-ttu-id="cc4c0-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="cc4c0-106">\<authenticationModules></span></span>  
<span data-ttu-id="cc4c0-107">\<add></span><span class="sxs-lookup"><span data-stu-id="cc4c0-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc4c0-108">語法</span><span class="sxs-lookup"><span data-stu-id="cc4c0-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc4c0-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cc4c0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cc4c0-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cc4c0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc4c0-111">屬性</span><span class="sxs-lookup"><span data-stu-id="cc4c0-111">Attributes</span></span>  
  
|<span data-ttu-id="cc4c0-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="cc4c0-112">**Attribute**</span></span>|<span data-ttu-id="cc4c0-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="cc4c0-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="cc4c0-114">完整型別名稱 (以<xref:System.Type.FullName%2A>屬性工作表示) 和元件名稱 (以<xref:System.Reflection.Assembly.FullName%2A>屬性工作表示), 並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="cc4c0-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc4c0-115">子元素</span><span class="sxs-lookup"><span data-stu-id="cc4c0-115">Child Elements</span></span>  
 <span data-ttu-id="cc4c0-116">無。</span><span class="sxs-lookup"><span data-stu-id="cc4c0-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc4c0-117">父項目</span><span class="sxs-lookup"><span data-stu-id="cc4c0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="cc4c0-118">**目**</span><span class="sxs-lookup"><span data-stu-id="cc4c0-118">**Element**</span></span>|<span data-ttu-id="cc4c0-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="cc4c0-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cc4c0-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="cc4c0-120">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="cc4c0-121">指定用來驗證網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="cc4c0-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc4c0-122">備註</span><span class="sxs-lookup"><span data-stu-id="cc4c0-122">Remarks</span></span>  
 <span data-ttu-id="cc4c0-123">`add` 項目會將驗證模組加入至已註冊驗證模組清單的尾端。</span><span class="sxs-lookup"><span data-stu-id="cc4c0-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="cc4c0-124">驗證模組會依其加入清單的順序來進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="cc4c0-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="cc4c0-125">`type`屬性的值應該是有效的型別名稱和對應的元件名稱, 並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="cc4c0-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cc4c0-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="cc4c0-126">Configuration Files</span></span>  
 <span data-ttu-id="cc4c0-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="cc4c0-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc4c0-128">範例</span><span class="sxs-lookup"><span data-stu-id="cc4c0-128">Example</span></span>  
 <span data-ttu-id="cc4c0-129">下列範例會啟用預設的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="cc4c0-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="cc4c0-130">您應該將 Version 和 PublicKeyToken 的值取代為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="cc4c0-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
        <authenticationModules>  
            <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NegotiateClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.KerberosClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NtlmClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.BasicClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc4c0-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc4c0-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="cc4c0-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="cc4c0-132">Network Settings Schema</span></span>](index.md)

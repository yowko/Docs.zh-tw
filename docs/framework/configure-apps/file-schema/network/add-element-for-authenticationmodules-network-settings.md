---
title: '&lt;新增&gt;authenticationModules （網路設定） 的項目'
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 471e36bb584164b851e7a06c0e682ba9872f7910
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742896"
---
# <a name="ltaddgt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="b8702-102">&lt;新增&gt;authenticationModules （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="b8702-102">&lt;add&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="b8702-103">將驗證模組加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8702-103">Adds an authentication module to the application.</span></span>  
  
 <span data-ttu-id="b8702-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b8702-104">\<configuration></span></span>  
<span data-ttu-id="b8702-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b8702-105">\<system.net></span></span>  
<span data-ttu-id="b8702-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="b8702-106">\<authenticationModules></span></span>  
<span data-ttu-id="b8702-107">\<add></span><span class="sxs-lookup"><span data-stu-id="b8702-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8702-108">語法</span><span class="sxs-lookup"><span data-stu-id="b8702-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8702-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b8702-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b8702-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b8702-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8702-111">屬性</span><span class="sxs-lookup"><span data-stu-id="b8702-111">Attributes</span></span>  
  
|<span data-ttu-id="b8702-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="b8702-112">**Attribute**</span></span>|<span data-ttu-id="b8702-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="b8702-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="b8702-114">完整限定的類型名稱 (由<xref:System.Type.FullName%2A>屬性) 和組件名稱 (由<xref:System.Reflection.Assembly.FullName%2A>屬性)、 以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="b8702-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8702-115">子項目</span><span class="sxs-lookup"><span data-stu-id="b8702-115">Child Elements</span></span>  
 <span data-ttu-id="b8702-116">無。</span><span class="sxs-lookup"><span data-stu-id="b8702-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8702-117">父項目</span><span class="sxs-lookup"><span data-stu-id="b8702-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b8702-118">**目**</span><span class="sxs-lookup"><span data-stu-id="b8702-118">**Element**</span></span>|<span data-ttu-id="b8702-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="b8702-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b8702-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="b8702-120">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="b8702-121">指定用來驗證網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="b8702-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8702-122">備註</span><span class="sxs-lookup"><span data-stu-id="b8702-122">Remarks</span></span>  
 <span data-ttu-id="b8702-123">`add` 項目會將驗證模組加入至已註冊驗證模組清單的尾端。</span><span class="sxs-lookup"><span data-stu-id="b8702-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="b8702-124">已加入至清單的順序，會呼叫驗證模組。</span><span class="sxs-lookup"><span data-stu-id="b8702-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="b8702-125">值`type`屬性應為有效型別名稱和對應的組件名稱，以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="b8702-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b8702-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="b8702-126">Configuration Files</span></span>  
 <span data-ttu-id="b8702-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="b8702-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8702-128">範例</span><span class="sxs-lookup"><span data-stu-id="b8702-128">Example</span></span>  
 <span data-ttu-id="b8702-129">下列範例會啟用預設的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="b8702-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="b8702-130">您應該取得版本和 PublicKeyToken 的值取代為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="b8702-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b8702-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8702-131">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="b8702-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b8702-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

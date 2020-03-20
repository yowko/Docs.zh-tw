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
ms.openlocfilehash: 4181a045079bdb455a63ebda722dd6b0daf33c4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155111"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="6bb9a-102">\<添加>元素以進行身份驗證模組（網路設置）</span><span class="sxs-lookup"><span data-stu-id="6bb9a-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="6bb9a-103">向應用程式添加身份驗證模組。</span><span class="sxs-lookup"><span data-stu-id="6bb9a-103">Adds an authentication module to the application.</span></span>  

<span data-ttu-id="6bb9a-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6bb9a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6bb9a-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6bb9a-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="6bb9a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份驗證模組>**](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6bb9a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="6bb9a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<添加>**</span><span class="sxs-lookup"><span data-stu-id="6bb9a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6bb9a-108">語法</span><span class="sxs-lookup"><span data-stu-id="6bb9a-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6bb9a-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6bb9a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6bb9a-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6bb9a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6bb9a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6bb9a-111">Attributes</span></span>  
  
|<span data-ttu-id="6bb9a-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="6bb9a-112">**Attribute**</span></span>|<span data-ttu-id="6bb9a-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="6bb9a-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="6bb9a-114">完全限定的類型名稱（由<xref:System.Type.FullName%2A>屬性指示）和程式集名稱（由<xref:System.Reflection.Assembly.FullName%2A>屬性指示），用逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="6bb9a-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6bb9a-115">子元素</span><span class="sxs-lookup"><span data-stu-id="6bb9a-115">Child Elements</span></span>  
 <span data-ttu-id="6bb9a-116">無。</span><span class="sxs-lookup"><span data-stu-id="6bb9a-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6bb9a-117">父項目</span><span class="sxs-lookup"><span data-stu-id="6bb9a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6bb9a-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="6bb9a-118">**Element**</span></span>|<span data-ttu-id="6bb9a-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="6bb9a-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6bb9a-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="6bb9a-120">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="6bb9a-121">指定用於驗證網路請求的模組。</span><span class="sxs-lookup"><span data-stu-id="6bb9a-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bb9a-122">備註</span><span class="sxs-lookup"><span data-stu-id="6bb9a-122">Remarks</span></span>  
 <span data-ttu-id="6bb9a-123">`add` 項目會將驗證模組加入至已註冊驗證模組清單的尾端。</span><span class="sxs-lookup"><span data-stu-id="6bb9a-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="6bb9a-124">身份驗證模組按添加到清單的順序調用。</span><span class="sxs-lookup"><span data-stu-id="6bb9a-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="6bb9a-125">`type`屬性的值應是有效的類型名稱和相應的程式集名稱，用逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="6bb9a-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6bb9a-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="6bb9a-126">Configuration Files</span></span>  
 <span data-ttu-id="6bb9a-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="6bb9a-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bb9a-128">範例</span><span class="sxs-lookup"><span data-stu-id="6bb9a-128">Example</span></span>  
 <span data-ttu-id="6bb9a-129">以下示例啟用預設身份驗證模組。</span><span class="sxs-lookup"><span data-stu-id="6bb9a-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="6bb9a-130">應將版本和 PublicKeyToken 的值替換為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="6bb9a-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6bb9a-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bb9a-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="6bb9a-132">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="6bb9a-132">Network Settings Schema</span></span>](index.md)

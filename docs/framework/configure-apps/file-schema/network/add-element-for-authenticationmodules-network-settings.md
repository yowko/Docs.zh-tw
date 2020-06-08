---
title: authenticationModules 的 <add> 項目 (網路設定)
description: <add>Connectionmanagement 專案的網路設定元素會將 IP 位址或 DNS 名稱新增至 .NET Framework 中的連接管理清單。
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
ms.openlocfilehash: 1a6d0f79f076a69cec33ac14f0e0f33f7c3c6577
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504637"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="d8558-103">authenticationModules 的 \<add> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="d8558-103">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="d8558-104">將驗證模組新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8558-104">Adds an authentication module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="d8558-105">語法</span><span class="sxs-lookup"><span data-stu-id="d8558-105">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8558-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d8558-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d8558-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d8558-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8558-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d8558-108">Attributes</span></span>  
  
|<span data-ttu-id="d8558-109">**屬性**</span><span class="sxs-lookup"><span data-stu-id="d8558-109">**Attribute**</span></span>|<span data-ttu-id="d8558-110">**描述**</span><span class="sxs-lookup"><span data-stu-id="d8558-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="d8558-111">完整型別名稱（以 <xref:System.Type.FullName%2A> 屬性工作表示）和元件名稱（以 <xref:System.Reflection.Assembly.FullName%2A> 屬性工作表示），並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="d8558-111">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8558-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d8558-112">Child Elements</span></span>  
 <span data-ttu-id="d8558-113">無。</span><span class="sxs-lookup"><span data-stu-id="d8558-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8558-114">父項目</span><span class="sxs-lookup"><span data-stu-id="d8558-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d8558-115">**元素**</span><span class="sxs-lookup"><span data-stu-id="d8558-115">**Element**</span></span>|<span data-ttu-id="d8558-116">**描述**</span><span class="sxs-lookup"><span data-stu-id="d8558-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d8558-117">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="d8558-117">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="d8558-118">指定用來驗證網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="d8558-118">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8558-119">備註</span><span class="sxs-lookup"><span data-stu-id="d8558-119">Remarks</span></span>  
 <span data-ttu-id="d8558-120">`add` 項目會將驗證模組加入至已註冊驗證模組清單的尾端。</span><span class="sxs-lookup"><span data-stu-id="d8558-120">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="d8558-121">驗證模組會依其加入清單的順序來進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="d8558-121">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="d8558-122">屬性的值 `type` 應該是有效的型別名稱和對應的元件名稱，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="d8558-122">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d8558-123">組態檔</span><span class="sxs-lookup"><span data-stu-id="d8558-123">Configuration Files</span></span>  
 <span data-ttu-id="d8558-124">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="d8558-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8558-125">範例</span><span class="sxs-lookup"><span data-stu-id="d8558-125">Example</span></span>  
 <span data-ttu-id="d8558-126">下列範例會啟用預設的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="d8558-126">The following example enables the default authentication modules.</span></span> <span data-ttu-id="d8558-127">您應該將 Version 和 PublicKeyToken 的值取代為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="d8558-127">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8558-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8558-128">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="d8558-129">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d8558-129">Network Settings Schema</span></span>](index.md)

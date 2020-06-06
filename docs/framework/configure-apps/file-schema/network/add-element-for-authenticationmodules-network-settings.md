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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155111"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="0f8d3-102">authenticationModules 的 \<add> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="0f8d3-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="0f8d3-103">將驗證模組新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f8d3-103">Adds an authentication module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="0f8d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="0f8d3-104">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f8d3-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0f8d3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0f8d3-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0f8d3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f8d3-107">屬性</span><span class="sxs-lookup"><span data-stu-id="0f8d3-107">Attributes</span></span>  
  
|<span data-ttu-id="0f8d3-108">**屬性**</span><span class="sxs-lookup"><span data-stu-id="0f8d3-108">**Attribute**</span></span>|<span data-ttu-id="0f8d3-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="0f8d3-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="0f8d3-110">完整型別名稱（以 <xref:System.Type.FullName%2A> 屬性工作表示）和元件名稱（以 <xref:System.Reflection.Assembly.FullName%2A> 屬性工作表示），並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="0f8d3-110">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f8d3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="0f8d3-111">Child Elements</span></span>  
 <span data-ttu-id="0f8d3-112">無。</span><span class="sxs-lookup"><span data-stu-id="0f8d3-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0f8d3-113">父項目</span><span class="sxs-lookup"><span data-stu-id="0f8d3-113">Parent Elements</span></span>  
  
|<span data-ttu-id="0f8d3-114">**元素**</span><span class="sxs-lookup"><span data-stu-id="0f8d3-114">**Element**</span></span>|<span data-ttu-id="0f8d3-115">**說明**</span><span class="sxs-lookup"><span data-stu-id="0f8d3-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0f8d3-116">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="0f8d3-116">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="0f8d3-117">指定用來驗證網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="0f8d3-117">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f8d3-118">備註</span><span class="sxs-lookup"><span data-stu-id="0f8d3-118">Remarks</span></span>  
 <span data-ttu-id="0f8d3-119">`add` 項目會將驗證模組加入至已註冊驗證模組清單的尾端。</span><span class="sxs-lookup"><span data-stu-id="0f8d3-119">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="0f8d3-120">驗證模組會依其加入清單的順序來進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="0f8d3-120">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="0f8d3-121">屬性的值 `type` 應該是有效的型別名稱和對應的元件名稱，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="0f8d3-121">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0f8d3-122">組態檔</span><span class="sxs-lookup"><span data-stu-id="0f8d3-122">Configuration Files</span></span>  
 <span data-ttu-id="0f8d3-123">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="0f8d3-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f8d3-124">範例</span><span class="sxs-lookup"><span data-stu-id="0f8d3-124">Example</span></span>  
 <span data-ttu-id="0f8d3-125">下列範例會啟用預設的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="0f8d3-125">The following example enables the default authentication modules.</span></span> <span data-ttu-id="0f8d3-126">您應該將 Version 和 PublicKeyToken 的值取代為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="0f8d3-126">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0f8d3-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f8d3-127">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="0f8d3-128">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0f8d3-128">Network Settings Schema</span></span>](index.md)

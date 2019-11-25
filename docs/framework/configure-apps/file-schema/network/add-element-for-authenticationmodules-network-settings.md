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
ms.openlocfilehash: 9c011cf1216b98fa20e330e185e4cf2c331b31d4
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087944"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="70d4d-102">\<為 Authenticationmodules 專案新增 > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="70d4d-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="70d4d-103">將驗證模組新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="70d4d-103">Adds an authentication module to the application.</span></span>  

<span data-ttu-id="70d4d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="70d4d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="70d4d-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="70d4d-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="70d4d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authenticationmodules 專案 >** ](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="70d4d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="70d4d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**新增 >**</span><span class="sxs-lookup"><span data-stu-id="70d4d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="70d4d-108">語法</span><span class="sxs-lookup"><span data-stu-id="70d4d-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70d4d-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="70d4d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="70d4d-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="70d4d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70d4d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="70d4d-111">Attributes</span></span>  
  
|<span data-ttu-id="70d4d-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="70d4d-112">**Attribute**</span></span>|<span data-ttu-id="70d4d-113">**說明**</span><span class="sxs-lookup"><span data-stu-id="70d4d-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="70d4d-114">完整型別名稱（以 <xref:System.Type.FullName%2A> 屬性工作表示）和元件名稱（以 <xref:System.Reflection.Assembly.FullName%2A> 屬性工作表示），並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="70d4d-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70d4d-115">子項目</span><span class="sxs-lookup"><span data-stu-id="70d4d-115">Child Elements</span></span>  
 <span data-ttu-id="70d4d-116">無。</span><span class="sxs-lookup"><span data-stu-id="70d4d-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70d4d-117">父項目</span><span class="sxs-lookup"><span data-stu-id="70d4d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="70d4d-118">**目**</span><span class="sxs-lookup"><span data-stu-id="70d4d-118">**Element**</span></span>|<span data-ttu-id="70d4d-119">**說明**</span><span class="sxs-lookup"><span data-stu-id="70d4d-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="70d4d-120">Authenticationmodules 專案</span><span class="sxs-lookup"><span data-stu-id="70d4d-120">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="70d4d-121">指定用來驗證網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="70d4d-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70d4d-122">備註</span><span class="sxs-lookup"><span data-stu-id="70d4d-122">Remarks</span></span>  
 <span data-ttu-id="70d4d-123">`add` 項目會將驗證模組加入至已註冊驗證模組清單的尾端。</span><span class="sxs-lookup"><span data-stu-id="70d4d-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="70d4d-124">驗證模組會依其加入清單的順序來進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="70d4d-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="70d4d-125">`type` 屬性的值應該是有效的型別名稱和對應的元件名稱，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="70d4d-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="70d4d-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="70d4d-126">Configuration Files</span></span>  
 <span data-ttu-id="70d4d-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="70d4d-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="70d4d-128">範例</span><span class="sxs-lookup"><span data-stu-id="70d4d-128">Example</span></span>  
 <span data-ttu-id="70d4d-129">下列範例會啟用預設的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="70d4d-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="70d4d-130">您應該將 Version 和 PublicKeyToken 的值取代為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="70d4d-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70d4d-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="70d4d-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="70d4d-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="70d4d-132">Network Settings Schema</span></span>](index.md)

---
title: <authenticationModules> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: b502cc4a0958f074018d4b0ce6b3fb118b811c2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154968"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="38acf-102">\<authenticationModules> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="38acf-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="38acf-103">指定用於驗證網路請求的模組。</span><span class="sxs-lookup"><span data-stu-id="38acf-103">Specifies modules used to authenticate network requests.</span></span>  

<span data-ttu-id="38acf-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="38acf-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="38acf-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="38acf-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="38acf-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<身份驗證模組>**</span><span class="sxs-lookup"><span data-stu-id="38acf-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**</span></span>

## <a name="syntax"></a><span data-ttu-id="38acf-107">語法</span><span class="sxs-lookup"><span data-stu-id="38acf-107">Syntax</span></span>  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38acf-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="38acf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="38acf-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="38acf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38acf-110">屬性</span><span class="sxs-lookup"><span data-stu-id="38acf-110">Attributes</span></span>  
 <span data-ttu-id="38acf-111">無。</span><span class="sxs-lookup"><span data-stu-id="38acf-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="38acf-112">子元素</span><span class="sxs-lookup"><span data-stu-id="38acf-112">Child Elements</span></span>  
  
|<span data-ttu-id="38acf-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="38acf-113">**Element**</span></span>|<span data-ttu-id="38acf-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="38acf-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="38acf-115">新增</span><span class="sxs-lookup"><span data-stu-id="38acf-115">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="38acf-116">向應用程式添加身份驗證模組。</span><span class="sxs-lookup"><span data-stu-id="38acf-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="38acf-117">清楚</span><span class="sxs-lookup"><span data-stu-id="38acf-117">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="38acf-118">清除應用程式中的所有身份驗證模組。</span><span class="sxs-lookup"><span data-stu-id="38acf-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="38acf-119">移除</span><span class="sxs-lookup"><span data-stu-id="38acf-119">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="38acf-120">從應用程式中刪除身份驗證模組。</span><span class="sxs-lookup"><span data-stu-id="38acf-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="38acf-121">父項目</span><span class="sxs-lookup"><span data-stu-id="38acf-121">Parent Elements</span></span>  
  
|<span data-ttu-id="38acf-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="38acf-122">**Element**</span></span>|<span data-ttu-id="38acf-123">**描述**</span><span class="sxs-lookup"><span data-stu-id="38acf-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="38acf-124">system.net</span><span class="sxs-lookup"><span data-stu-id="38acf-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="38acf-125">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="38acf-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38acf-126">備註</span><span class="sxs-lookup"><span data-stu-id="38acf-126">Remarks</span></span>  
 <span data-ttu-id="38acf-127">該`authenticationModule`元素指定使用伺服器執行身份驗證過程的身份驗證模組。</span><span class="sxs-lookup"><span data-stu-id="38acf-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="38acf-128">身份驗證模組必須實現<xref:System.Net.IAuthenticationModule>介面。</span><span class="sxs-lookup"><span data-stu-id="38acf-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="38acf-129">組態檔</span><span class="sxs-lookup"><span data-stu-id="38acf-129">Configuration Files</span></span>  
 <span data-ttu-id="38acf-130">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="38acf-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="38acf-131">範例</span><span class="sxs-lookup"><span data-stu-id="38acf-131">Example</span></span>  
 <span data-ttu-id="38acf-132">以下示例啟用身份驗證模組。</span><span class="sxs-lookup"><span data-stu-id="38acf-132">The following example enables an authentication module.</span></span> <span data-ttu-id="38acf-133">應將版本和 PublicKeyToken 的值替換為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="38acf-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="38acf-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38acf-134">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="38acf-135">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="38acf-135">Network Settings Schema</span></span>](index.md)

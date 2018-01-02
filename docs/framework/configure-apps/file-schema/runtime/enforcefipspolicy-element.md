---
title: "&lt;enforceFIPSPolicy&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fb8cb1ea4d011eb25aee14ddd53d3dc882f75d8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltenforcefipspolicygt-element"></a><span data-ttu-id="1cd3b-102">&lt;enforceFIPSPolicy&gt;項目</span><span class="sxs-lookup"><span data-stu-id="1cd3b-102">&lt;enforceFIPSPolicy&gt; Element</span></span>
<span data-ttu-id="1cd3b-103">指定是否強制執行電腦設定需求，以便讓密碼編譯演算法符合美國聯邦資訊處理標準 (FIPS) 的規範。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
 <span data-ttu-id="1cd3b-104">\<設定 > 項目</span><span class="sxs-lookup"><span data-stu-id="1cd3b-104">\<configuration> Element</span></span>  
<span data-ttu-id="1cd3b-105">\<runtime > 項目</span><span class="sxs-lookup"><span data-stu-id="1cd3b-105">\<runtime> Element</span></span>  
<span data-ttu-id="1cd3b-106">\<enforceFIPSPolicy > 項目</span><span class="sxs-lookup"><span data-stu-id="1cd3b-106">\<enforceFIPSPolicy> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cd3b-107">語法</span><span class="sxs-lookup"><span data-stu-id="1cd3b-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1cd3b-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1cd3b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1cd3b-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1cd3b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1cd3b-110">Attributes</span></span>  
  
|<span data-ttu-id="1cd3b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="1cd3b-111">Attribute</span></span>|<span data-ttu-id="1cd3b-112">描述</span><span class="sxs-lookup"><span data-stu-id="1cd3b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1cd3b-113">enabled</span><span class="sxs-lookup"><span data-stu-id="1cd3b-113">enabled</span></span>|<span data-ttu-id="1cd3b-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="1cd3b-115">指定是否要啟用 強制執行密碼編譯演算法必須與 FIPS 相容的電腦設定需求。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1cd3b-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="1cd3b-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="1cd3b-117">值</span><span class="sxs-lookup"><span data-stu-id="1cd3b-117">Value</span></span>|<span data-ttu-id="1cd3b-118">描述</span><span class="sxs-lookup"><span data-stu-id="1cd3b-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="1cd3b-119">如果您的電腦設定為需要與 FIPS 相容的密碼編譯演算法時，會強制執行這項需求。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="1cd3b-120">如果類別實作的演算法不會符合 FIPS，建構函式或`Create`該電腦上執行時，該類別的方法擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="1cd3b-121">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="1cd3b-122">密碼編譯演算法所使用的應用程式不一定要符合 FIPS，不論電腦組態。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1cd3b-123">子元素</span><span class="sxs-lookup"><span data-stu-id="1cd3b-123">Child Elements</span></span>  
 <span data-ttu-id="1cd3b-124">無。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1cd3b-125">父項目</span><span class="sxs-lookup"><span data-stu-id="1cd3b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="1cd3b-126">項目</span><span class="sxs-lookup"><span data-stu-id="1cd3b-126">Element</span></span>|<span data-ttu-id="1cd3b-127">描述</span><span class="sxs-lookup"><span data-stu-id="1cd3b-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1cd3b-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1cd3b-129">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1cd3b-130">備註</span><span class="sxs-lookup"><span data-stu-id="1cd3b-130">Remarks</span></span>  
 <span data-ttu-id="1cd3b-131">從.NET Framework 2.0 開始，實作密碼編譯演算法之類別的建立是由電腦的設定所控制。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="1cd3b-132">如果電腦已設定為需要演算法，以符合 FIPS，類別會實作與 FIPS 不相容的演算法，任何嘗試建立該類別的執行個體就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="1cd3b-133">建構函式會擲回<xref:System.InvalidOperationException>例外狀況，以及`Create`方法會擲回<xref:System.Reflection.TargetInvocationException>例外狀況，並傳回內部<xref:System.InvalidOperationException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="1cd3b-134">如果您的應用程式在其設定，都需要使用 FIPS，相容性的電腦上執行您的應用程式會使用與 FIPS 不相容的演算法，您可以防止 common language runtime (CLR) 來自組態檔中使用這個項目強制使用 FIPS 相容性。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="1cd3b-135">中引進這個項目[!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-135">This element was introduced in the [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cd3b-136">範例</span><span class="sxs-lookup"><span data-stu-id="1cd3b-136">Example</span></span>  
 <span data-ttu-id="1cd3b-137">下列範例會示範如何防止 CLR 強制使用 FIPS 相容性。</span><span class="sxs-lookup"><span data-stu-id="1cd3b-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1cd3b-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="1cd3b-138">See Also</span></span>  
 [<span data-ttu-id="1cd3b-139">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1cd3b-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="1cd3b-140">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="1cd3b-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="1cd3b-141">加密模型</span><span class="sxs-lookup"><span data-stu-id="1cd3b-141">Cryptography Model</span></span>](../../../../../docs/standard/security/cryptography-model.md)

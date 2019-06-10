---
title: <enforceFIPSPolicy> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c13dd2f00e08539d2ba502058c74aa4a1525e3ff
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816114"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="c6d78-102">\<enforceFIPSPolicy > 項目</span><span class="sxs-lookup"><span data-stu-id="c6d78-102">\<enforceFIPSPolicy> Element</span></span>
<span data-ttu-id="c6d78-103">指定是否強制執行電腦設定需求，以便讓密碼編譯演算法符合美國聯邦資訊處理標準 (FIPS) 的規範。</span><span class="sxs-lookup"><span data-stu-id="c6d78-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
 <span data-ttu-id="c6d78-104">\<組態 > 項目</span><span class="sxs-lookup"><span data-stu-id="c6d78-104">\<configuration> Element</span></span>  
<span data-ttu-id="c6d78-105">\<執行階段 > 項目</span><span class="sxs-lookup"><span data-stu-id="c6d78-105">\<runtime> Element</span></span>  
<span data-ttu-id="c6d78-106">\<enforceFIPSPolicy > 項目</span><span class="sxs-lookup"><span data-stu-id="c6d78-106">\<enforceFIPSPolicy> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6d78-107">語法</span><span class="sxs-lookup"><span data-stu-id="c6d78-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6d78-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c6d78-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c6d78-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c6d78-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6d78-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c6d78-110">Attributes</span></span>  
  
|<span data-ttu-id="c6d78-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c6d78-111">Attribute</span></span>|<span data-ttu-id="c6d78-112">描述</span><span class="sxs-lookup"><span data-stu-id="c6d78-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6d78-113">enabled</span><span class="sxs-lookup"><span data-stu-id="c6d78-113">enabled</span></span>|<span data-ttu-id="c6d78-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c6d78-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="c6d78-115">指定是否要啟用 強制執行密碼編譯演算法必須是符合 FIPS 規範的電腦設定需求。</span><span class="sxs-lookup"><span data-stu-id="c6d78-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c6d78-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="c6d78-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="c6d78-117">值</span><span class="sxs-lookup"><span data-stu-id="c6d78-117">Value</span></span>|<span data-ttu-id="c6d78-118">描述</span><span class="sxs-lookup"><span data-stu-id="c6d78-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="c6d78-119">如果您的電腦設定為需要與 FIPS 相容的密碼編譯演算法，會強制執行這項需求。</span><span class="sxs-lookup"><span data-stu-id="c6d78-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="c6d78-120">如果類別實作不符合 FIPS，建構函式是演算法或`Create`在該電腦上執行時，該類別的方法擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c6d78-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="c6d78-121">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="c6d78-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="c6d78-122">密碼編譯演算法所使用的應用程式不一定要符合 FIPS 規範，不論電腦設定。</span><span class="sxs-lookup"><span data-stu-id="c6d78-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6d78-123">子元素</span><span class="sxs-lookup"><span data-stu-id="c6d78-123">Child Elements</span></span>  
 <span data-ttu-id="c6d78-124">無。</span><span class="sxs-lookup"><span data-stu-id="c6d78-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6d78-125">父項目</span><span class="sxs-lookup"><span data-stu-id="c6d78-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c6d78-126">項目</span><span class="sxs-lookup"><span data-stu-id="c6d78-126">Element</span></span>|<span data-ttu-id="c6d78-127">描述</span><span class="sxs-lookup"><span data-stu-id="c6d78-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c6d78-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c6d78-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c6d78-129">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="c6d78-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6d78-130">備註</span><span class="sxs-lookup"><span data-stu-id="c6d78-130">Remarks</span></span>  
 <span data-ttu-id="c6d78-131">從.NET Framework 2.0 開始，實作密碼編譯演算法之類別的建立是由電腦的設定所控制。</span><span class="sxs-lookup"><span data-stu-id="c6d78-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="c6d78-132">如果電腦已設定為需要演算法，以符合 FIPS，類別會實作不會符合 FIPS 規範的演算法，任何嘗試建立該類別的執行個體就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c6d78-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="c6d78-133">建構函式會擲回<xref:System.InvalidOperationException>例外狀況，並`Create`方法會擲回<xref:System.Reflection.TargetInvocationException>例外狀況，並傳回內部<xref:System.InvalidOperationException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c6d78-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="c6d78-134">如果您的應用程式在其組態需要 fips，合規性的電腦上執行您的應用程式會使用與 FIPS 不相容的演算法，您可以使用您的組態檔的這個項目以防止從的 common language runtime (CLR)強制執行的 FIPS 合規性。</span><span class="sxs-lookup"><span data-stu-id="c6d78-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="c6d78-135">.NET Framework 2.0 Service Pack 1 中引進了這個項目。</span><span class="sxs-lookup"><span data-stu-id="c6d78-135">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6d78-136">範例</span><span class="sxs-lookup"><span data-stu-id="c6d78-136">Example</span></span>  
 <span data-ttu-id="c6d78-137">下列範例示範如何防止 CLR 強制 FIPS 合規性。</span><span class="sxs-lookup"><span data-stu-id="c6d78-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6d78-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6d78-138">See also</span></span>

- [<span data-ttu-id="c6d78-139">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c6d78-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="c6d78-140">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="c6d78-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="c6d78-141">加密模型</span><span class="sxs-lookup"><span data-stu-id="c6d78-141">Cryptography Model</span></span>](../../../../../docs/standard/security/cryptography-model.md)

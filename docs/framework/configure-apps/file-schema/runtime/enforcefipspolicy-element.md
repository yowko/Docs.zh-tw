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
ms.openlocfilehash: eb28eddf7e9f13bceaf47de28633073f59f3920d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663748"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="e2688-102">\<enforceFIPSPolicy > 元素</span><span class="sxs-lookup"><span data-stu-id="e2688-102">\<enforceFIPSPolicy> Element</span></span>
<span data-ttu-id="e2688-103">指定是否強制執行電腦設定需求，以便讓密碼編譯演算法符合美國聯邦資訊處理標準 (FIPS) 的規範。</span><span class="sxs-lookup"><span data-stu-id="e2688-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
 <span data-ttu-id="e2688-104">\<configuration > 元素</span><span class="sxs-lookup"><span data-stu-id="e2688-104">\<configuration> Element</span></span>  
<span data-ttu-id="e2688-105">\<執行時間 > 元素</span><span class="sxs-lookup"><span data-stu-id="e2688-105">\<runtime> Element</span></span>  
<span data-ttu-id="e2688-106">\<enforceFIPSPolicy > 元素</span><span class="sxs-lookup"><span data-stu-id="e2688-106">\<enforceFIPSPolicy> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2688-107">語法</span><span class="sxs-lookup"><span data-stu-id="e2688-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2688-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e2688-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e2688-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e2688-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2688-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e2688-110">Attributes</span></span>  
  
|<span data-ttu-id="e2688-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e2688-111">Attribute</span></span>|<span data-ttu-id="e2688-112">描述</span><span class="sxs-lookup"><span data-stu-id="e2688-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2688-113">enabled</span><span class="sxs-lookup"><span data-stu-id="e2688-113">enabled</span></span>|<span data-ttu-id="e2688-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="e2688-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="e2688-115">指定是否要啟用電腦設定需求, 而密碼編譯演算法必須符合 FIPS 規範。</span><span class="sxs-lookup"><span data-stu-id="e2688-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e2688-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="e2688-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="e2688-117">值</span><span class="sxs-lookup"><span data-stu-id="e2688-117">Value</span></span>|<span data-ttu-id="e2688-118">描述</span><span class="sxs-lookup"><span data-stu-id="e2688-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="e2688-119">如果您的電腦設定為要求密碼編譯演算法符合 FIPS 規範, 則會強制執行該需求。</span><span class="sxs-lookup"><span data-stu-id="e2688-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="e2688-120">如果類別會執行不符合 FIPS 規範的演算法, 則該類別的函`Create`式或方法會在該電腦上執行時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e2688-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="e2688-121">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="e2688-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="e2688-122">無論電腦設定為何, 應用程式所使用的密碼編譯演算法都不需要符合 FIPS。</span><span class="sxs-lookup"><span data-stu-id="e2688-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2688-123">子元素</span><span class="sxs-lookup"><span data-stu-id="e2688-123">Child Elements</span></span>  
 <span data-ttu-id="e2688-124">無。</span><span class="sxs-lookup"><span data-stu-id="e2688-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e2688-125">父項目</span><span class="sxs-lookup"><span data-stu-id="e2688-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e2688-126">項目</span><span class="sxs-lookup"><span data-stu-id="e2688-126">Element</span></span>|<span data-ttu-id="e2688-127">說明</span><span class="sxs-lookup"><span data-stu-id="e2688-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e2688-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="e2688-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e2688-129">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="e2688-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2688-130">備註</span><span class="sxs-lookup"><span data-stu-id="e2688-130">Remarks</span></span>  
 <span data-ttu-id="e2688-131">從 .NET Framework 2.0 開始, 建立執行密碼編譯演算法的類別是由電腦的設定所控制。</span><span class="sxs-lookup"><span data-stu-id="e2688-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="e2688-132">如果電腦設定為要求演算法必須符合 FIPS, 而且類別會執行不符合 FIPS 規範的演算法, 則嘗試建立該類別的實例會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e2688-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="e2688-133">函式<xref:System.InvalidOperationException>會擲回例外`Create`狀況, 而<xref:System.Reflection.TargetInvocationException>方法會擲回<xref:System.InvalidOperationException>具有內部例外狀況的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e2688-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="e2688-134">如果您的應用程式在設定需要符合 FIPS 規範的電腦上執行, 而且您的應用程式使用不符合 FIPS 規範的演算法, 您可以在設定檔案中使用這個元素, 以防止 common language runtime (CLR)強制執行 FIPS 合規性。</span><span class="sxs-lookup"><span data-stu-id="e2688-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="e2688-135">此元素是在 .NET Framework 2.0 Service Pack 1 中引進。</span><span class="sxs-lookup"><span data-stu-id="e2688-135">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2688-136">範例</span><span class="sxs-lookup"><span data-stu-id="e2688-136">Example</span></span>  
 <span data-ttu-id="e2688-137">下列範例顯示如何防止 CLR 強制執行 FIPS 合規性。</span><span class="sxs-lookup"><span data-stu-id="e2688-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2688-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2688-138">See also</span></span>

- [<span data-ttu-id="e2688-139">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e2688-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e2688-140">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="e2688-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e2688-141">加密模型</span><span class="sxs-lookup"><span data-stu-id="e2688-141">Cryptography Model</span></span>](../../../../../docs/standard/security/cryptography-model.md)

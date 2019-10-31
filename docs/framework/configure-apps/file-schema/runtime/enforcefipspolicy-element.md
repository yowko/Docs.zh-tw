---
title: <enforceFIPSPolicy> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
ms.openlocfilehash: 0d6dd291a24928487a040c0427f058dee80bf836
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117378"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="68ec9-102">\<enforceFIPSPolicy > 元素</span><span class="sxs-lookup"><span data-stu-id="68ec9-102">\<enforceFIPSPolicy> Element</span></span>
<span data-ttu-id="68ec9-103">指定是否強制執行電腦設定需求，以便讓密碼編譯演算法符合美國聯邦資訊處理標準 (FIPS) 的規範。</span><span class="sxs-lookup"><span data-stu-id="68ec9-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
<span data-ttu-id="68ec9-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="68ec9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="68ec9-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="68ec9-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="68ec9-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<enforceFIPSPolicy >**</span><span class="sxs-lookup"><span data-stu-id="68ec9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<enforceFIPSPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68ec9-107">語法</span><span class="sxs-lookup"><span data-stu-id="68ec9-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68ec9-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="68ec9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="68ec9-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="68ec9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68ec9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="68ec9-110">Attributes</span></span>  
  
|<span data-ttu-id="68ec9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="68ec9-111">Attribute</span></span>|<span data-ttu-id="68ec9-112">描述</span><span class="sxs-lookup"><span data-stu-id="68ec9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68ec9-113">enabled</span><span class="sxs-lookup"><span data-stu-id="68ec9-113">enabled</span></span>|<span data-ttu-id="68ec9-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="68ec9-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="68ec9-115">指定是否要啟用電腦設定需求，而密碼編譯演算法必須符合 FIPS 規範。</span><span class="sxs-lookup"><span data-stu-id="68ec9-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="68ec9-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="68ec9-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="68ec9-117">值</span><span class="sxs-lookup"><span data-stu-id="68ec9-117">Value</span></span>|<span data-ttu-id="68ec9-118">描述</span><span class="sxs-lookup"><span data-stu-id="68ec9-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="68ec9-119">如果您的電腦設定為要求密碼編譯演算法符合 FIPS 規範，則會強制執行該需求。</span><span class="sxs-lookup"><span data-stu-id="68ec9-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="68ec9-120">如果類別所執行的演算法與 FIPS 不相容，則該類別的函式或 `Create` 方法會在該電腦上執行時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="68ec9-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="68ec9-121">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="68ec9-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="68ec9-122">無論電腦設定為何，應用程式所使用的密碼編譯演算法都不需要符合 FIPS。</span><span class="sxs-lookup"><span data-stu-id="68ec9-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68ec9-123">子項目</span><span class="sxs-lookup"><span data-stu-id="68ec9-123">Child Elements</span></span>  
 <span data-ttu-id="68ec9-124">無。</span><span class="sxs-lookup"><span data-stu-id="68ec9-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="68ec9-125">父項目</span><span class="sxs-lookup"><span data-stu-id="68ec9-125">Parent Elements</span></span>  
  
|<span data-ttu-id="68ec9-126">項目</span><span class="sxs-lookup"><span data-stu-id="68ec9-126">Element</span></span>|<span data-ttu-id="68ec9-127">描述</span><span class="sxs-lookup"><span data-stu-id="68ec9-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="68ec9-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="68ec9-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="68ec9-129">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="68ec9-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68ec9-130">備註</span><span class="sxs-lookup"><span data-stu-id="68ec9-130">Remarks</span></span>  
 <span data-ttu-id="68ec9-131">從 .NET Framework 2.0 開始，建立執行密碼編譯演算法的類別是由電腦的設定所控制。</span><span class="sxs-lookup"><span data-stu-id="68ec9-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="68ec9-132">如果電腦設定為要求演算法必須符合 FIPS，而且類別會執行不符合 FIPS 規範的演算法，則嘗試建立該類別的實例會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="68ec9-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="68ec9-133">函式會擲回 <xref:System.InvalidOperationException> 例外狀況，而 `Create` 方法會擲回具有內部 <xref:System.InvalidOperationException> 例外狀況的 <xref:System.Reflection.TargetInvocationException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="68ec9-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="68ec9-134">如果您的應用程式在設定需要符合 FIPS 規範的電腦上執行，而且您的應用程式使用不符合 FIPS 規範的演算法，您可以在設定檔案中使用這個元素，以防止 common language runtime （CLR）強制執行 FIPS 合規性。</span><span class="sxs-lookup"><span data-stu-id="68ec9-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="68ec9-135">此元素是在 .NET Framework 2.0 Service Pack 1 中引進。</span><span class="sxs-lookup"><span data-stu-id="68ec9-135">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68ec9-136">範例</span><span class="sxs-lookup"><span data-stu-id="68ec9-136">Example</span></span>  
 <span data-ttu-id="68ec9-137">下列範例顯示如何防止 CLR 強制執行 FIPS 合規性。</span><span class="sxs-lookup"><span data-stu-id="68ec9-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="68ec9-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="68ec9-138">See also</span></span>

- [<span data-ttu-id="68ec9-139">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="68ec9-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="68ec9-140">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="68ec9-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="68ec9-141">加密模型</span><span class="sxs-lookup"><span data-stu-id="68ec9-141">Cryptography Model</span></span>](../../../../standard/security/cryptography-model.md)

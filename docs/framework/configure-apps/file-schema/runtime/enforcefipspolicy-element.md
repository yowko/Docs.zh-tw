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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117378"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="86d8d-102">\<enforceFIPSPolicy> 項目</span><span class="sxs-lookup"><span data-stu-id="86d8d-102">\<enforceFIPSPolicy> Element</span></span>
<span data-ttu-id="86d8d-103">指定是否強制執行電腦設定需求，以便讓密碼編譯演算法符合美國聯邦資訊處理標準 (FIPS) 的規範。</span><span class="sxs-lookup"><span data-stu-id="86d8d-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<enforceFIPSPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="86d8d-104">語法</span><span class="sxs-lookup"><span data-stu-id="86d8d-104">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86d8d-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="86d8d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="86d8d-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="86d8d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86d8d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="86d8d-107">Attributes</span></span>  
  
|<span data-ttu-id="86d8d-108">屬性</span><span class="sxs-lookup"><span data-stu-id="86d8d-108">Attribute</span></span>|<span data-ttu-id="86d8d-109">描述</span><span class="sxs-lookup"><span data-stu-id="86d8d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86d8d-110">已啟用</span><span class="sxs-lookup"><span data-stu-id="86d8d-110">enabled</span></span>|<span data-ttu-id="86d8d-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="86d8d-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="86d8d-112">指定是否要啟用電腦設定需求，而密碼編譯演算法必須符合 FIPS 規範。</span><span class="sxs-lookup"><span data-stu-id="86d8d-112">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="86d8d-113">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="86d8d-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="86d8d-114">值</span><span class="sxs-lookup"><span data-stu-id="86d8d-114">Value</span></span>|<span data-ttu-id="86d8d-115">描述</span><span class="sxs-lookup"><span data-stu-id="86d8d-115">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="86d8d-116">如果您的電腦設定為要求密碼編譯演算法符合 FIPS 規範，則會強制執行該需求。</span><span class="sxs-lookup"><span data-stu-id="86d8d-116">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="86d8d-117">如果類別會執行不符合 FIPS 規範的演算法，則該類別的函式或 `Create` 方法會在該電腦上執行時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="86d8d-117">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="86d8d-118">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="86d8d-118">This is the default.</span></span>|  
|`false`|<span data-ttu-id="86d8d-119">無論電腦設定為何，應用程式所使用的密碼編譯演算法都不需要符合 FIPS。</span><span class="sxs-lookup"><span data-stu-id="86d8d-119">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86d8d-120">子元素</span><span class="sxs-lookup"><span data-stu-id="86d8d-120">Child Elements</span></span>  
 <span data-ttu-id="86d8d-121">無。</span><span class="sxs-lookup"><span data-stu-id="86d8d-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86d8d-122">父項目</span><span class="sxs-lookup"><span data-stu-id="86d8d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="86d8d-123">元素</span><span class="sxs-lookup"><span data-stu-id="86d8d-123">Element</span></span>|<span data-ttu-id="86d8d-124">描述</span><span class="sxs-lookup"><span data-stu-id="86d8d-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="86d8d-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="86d8d-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="86d8d-126">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="86d8d-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86d8d-127">備註</span><span class="sxs-lookup"><span data-stu-id="86d8d-127">Remarks</span></span>  
 <span data-ttu-id="86d8d-128">從 .NET Framework 2.0 開始，建立執行密碼編譯演算法的類別是由電腦的設定所控制。</span><span class="sxs-lookup"><span data-stu-id="86d8d-128">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="86d8d-129">如果電腦設定為要求演算法必須符合 FIPS，而且類別會執行不符合 FIPS 規範的演算法，則嘗試建立該類別的實例會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="86d8d-129">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="86d8d-130">函式會擲回 <xref:System.InvalidOperationException> 例外狀況，而 `Create` 方法會擲回 <xref:System.Reflection.TargetInvocationException> 具有內部 <xref:System.InvalidOperationException> 例外狀況的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="86d8d-130">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="86d8d-131">如果您的應用程式在設定需要符合 FIPS 規範的電腦上執行，而且您的應用程式使用不符合 FIPS 規範的演算法，您可以在設定檔案中使用這個專案，以防止 common language runtime （CLR）強制執行 FIPS 合規性。</span><span class="sxs-lookup"><span data-stu-id="86d8d-131">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="86d8d-132">此元素是在 .NET Framework 2.0 Service Pack 1 中引進。</span><span class="sxs-lookup"><span data-stu-id="86d8d-132">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86d8d-133">範例</span><span class="sxs-lookup"><span data-stu-id="86d8d-133">Example</span></span>  
 <span data-ttu-id="86d8d-134">下列範例顯示如何防止 CLR 強制執行 FIPS 合規性。</span><span class="sxs-lookup"><span data-stu-id="86d8d-134">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="86d8d-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86d8d-135">See also</span></span>

- [<span data-ttu-id="86d8d-136">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="86d8d-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="86d8d-137">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="86d8d-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="86d8d-138">加密模型</span><span class="sxs-lookup"><span data-stu-id="86d8d-138">Cryptography Model</span></span>](../../../../standard/security/cryptography-model.md)

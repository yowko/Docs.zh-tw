---
title: '&lt;cryptoNameMapping&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ef916b0950e179f6782ce8d4d6fa380fd3804aa0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577162"
---
# <a name="ltcryptonamemappinggt-element"></a><span data-ttu-id="18775-102">&lt;cryptoNameMapping&gt;項目</span><span class="sxs-lookup"><span data-stu-id="18775-102">&lt;cryptoNameMapping&gt; Element</span></span>
<span data-ttu-id="18775-103">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="18775-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="18775-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="18775-104">\<configuration></span></span>  
<span data-ttu-id="18775-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="18775-105">\<mscorlib></span></span>  
<span data-ttu-id="18775-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="18775-106">\<cryptographySettings></span></span>  
<span data-ttu-id="18775-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="18775-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18775-108">語法</span><span class="sxs-lookup"><span data-stu-id="18775-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18775-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="18775-109">Attributes and Elements</span></span>  
 <span data-ttu-id="18775-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="18775-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18775-111">屬性</span><span class="sxs-lookup"><span data-stu-id="18775-111">Attributes</span></span>  
 <span data-ttu-id="18775-112">無。</span><span class="sxs-lookup"><span data-stu-id="18775-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="18775-113">子元素</span><span class="sxs-lookup"><span data-stu-id="18775-113">Child Elements</span></span>  
  
|<span data-ttu-id="18775-114">項目</span><span class="sxs-lookup"><span data-stu-id="18775-114">Element</span></span>|<span data-ttu-id="18775-115">描述</span><span class="sxs-lookup"><span data-stu-id="18775-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="18775-116">包含密碼編譯類別清單，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="18775-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="18775-117">將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。</span><span class="sxs-lookup"><span data-stu-id="18775-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="18775-118">父項目</span><span class="sxs-lookup"><span data-stu-id="18775-118">Parent Elements</span></span>  
  
|<span data-ttu-id="18775-119">項目</span><span class="sxs-lookup"><span data-stu-id="18775-119">Element</span></span>|<span data-ttu-id="18775-120">描述</span><span class="sxs-lookup"><span data-stu-id="18775-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="18775-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="18775-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="18775-122">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="18775-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="18775-123">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="18775-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="18775-124">包含\<cryptographySettings > 項目。</span><span class="sxs-lookup"><span data-stu-id="18775-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="18775-125">範例</span><span class="sxs-lookup"><span data-stu-id="18775-125">Example</span></span>  
 <span data-ttu-id="18775-126">下列範例示範如何使用 **\<cryptoNameMapping >** 項目參考加密編譯類別及設定執行階段。</span><span class="sxs-lookup"><span data-stu-id="18775-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="18775-127">然後，您可以將字串"RSA"傳遞至<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法和用法<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>方法來傳回`MyCryptoRSAClass`物件。</span><span class="sxs-lookup"><span data-stu-id="18775-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="18775-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18775-128">See also</span></span>
- [<span data-ttu-id="18775-129">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="18775-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="18775-130">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="18775-130">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="18775-131">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="18775-131">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="18775-132">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="18775-132">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)

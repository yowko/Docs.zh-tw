---
title: <cryptoNameMapping> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: 87b24595f5013ad3b981256fd97bc758863c600b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921105"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="6e3c0-102">\<cryptoNameMapping > 元素</span><span class="sxs-lookup"><span data-stu-id="6e3c0-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="6e3c0-103">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="6e3c0-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="6e3c0-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6e3c0-104">\<configuration></span></span>  
<span data-ttu-id="6e3c0-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="6e3c0-105">\<mscorlib></span></span>  
<span data-ttu-id="6e3c0-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="6e3c0-106">\<cryptographySettings></span></span>  
<span data-ttu-id="6e3c0-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="6e3c0-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e3c0-108">語法</span><span class="sxs-lookup"><span data-stu-id="6e3c0-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e3c0-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6e3c0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6e3c0-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6e3c0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e3c0-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6e3c0-111">Attributes</span></span>  
 <span data-ttu-id="6e3c0-112">無。</span><span class="sxs-lookup"><span data-stu-id="6e3c0-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6e3c0-113">子元素</span><span class="sxs-lookup"><span data-stu-id="6e3c0-113">Child Elements</span></span>  
  
|<span data-ttu-id="6e3c0-114">項目</span><span class="sxs-lookup"><span data-stu-id="6e3c0-114">Element</span></span>|<span data-ttu-id="6e3c0-115">描述</span><span class="sxs-lookup"><span data-stu-id="6e3c0-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="6e3c0-116">包含密碼編譯類別清單，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="6e3c0-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="6e3c0-117">將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。</span><span class="sxs-lookup"><span data-stu-id="6e3c0-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6e3c0-118">父項目</span><span class="sxs-lookup"><span data-stu-id="6e3c0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6e3c0-119">項目</span><span class="sxs-lookup"><span data-stu-id="6e3c0-119">Element</span></span>|<span data-ttu-id="6e3c0-120">說明</span><span class="sxs-lookup"><span data-stu-id="6e3c0-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6e3c0-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="6e3c0-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="6e3c0-122">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="6e3c0-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="6e3c0-123">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="6e3c0-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="6e3c0-124">\<包含 cryptographySettings > 元素。</span><span class="sxs-lookup"><span data-stu-id="6e3c0-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6e3c0-125">範例</span><span class="sxs-lookup"><span data-stu-id="6e3c0-125">Example</span></span>  
 <span data-ttu-id="6e3c0-126">下列範例示範如何使用 **\<cryptoNameMapping >** 元素來參考密碼編譯類別, 以及設定執行時間。</span><span class="sxs-lookup"><span data-stu-id="6e3c0-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="6e3c0-127">接著, 您可以將字串 "RSA" 傳遞給<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法, 並<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>使用方法來`MyCryptoRSAClass`傳回物件。</span><span class="sxs-lookup"><span data-stu-id="6e3c0-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e3c0-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e3c0-128">See also</span></span>

- [<span data-ttu-id="6e3c0-129">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="6e3c0-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6e3c0-130">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6e3c0-130">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6e3c0-131">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="6e3c0-131">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="6e3c0-132">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="6e3c0-132">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

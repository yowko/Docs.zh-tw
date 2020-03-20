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
ms.openlocfilehash: d31c5cd52ffe0e2a6eb5784735e76436d216444b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155215"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="cf2da-102">\<加密名稱映射>元素</span><span class="sxs-lookup"><span data-stu-id="cf2da-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="cf2da-103">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="cf2da-103">Contains mappings of classes to friendly names.</span></span>  

<span data-ttu-id="cf2da-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cf2da-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cf2da-105">&nbsp;&nbsp;[**\<姆斯科利布>**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="cf2da-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="cf2da-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<密碼設置>**](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="cf2da-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="cf2da-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<加密名稱映射>**</span><span class="sxs-lookup"><span data-stu-id="cf2da-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**</span></span>

## <a name="syntax"></a><span data-ttu-id="cf2da-108">語法</span><span class="sxs-lookup"><span data-stu-id="cf2da-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf2da-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cf2da-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cf2da-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cf2da-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf2da-111">屬性</span><span class="sxs-lookup"><span data-stu-id="cf2da-111">Attributes</span></span>  
 <span data-ttu-id="cf2da-112">無。</span><span class="sxs-lookup"><span data-stu-id="cf2da-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cf2da-113">子元素</span><span class="sxs-lookup"><span data-stu-id="cf2da-113">Child Elements</span></span>  
  
|<span data-ttu-id="cf2da-114">元素</span><span class="sxs-lookup"><span data-stu-id="cf2da-114">Element</span></span>|<span data-ttu-id="cf2da-115">描述</span><span class="sxs-lookup"><span data-stu-id="cf2da-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="cf2da-116">包含具有映射到**\<nameentry>** 元素中的易記名稱的加密類的清單。</span><span class="sxs-lookup"><span data-stu-id="cf2da-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="cf2da-117">將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。</span><span class="sxs-lookup"><span data-stu-id="cf2da-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf2da-118">父項目</span><span class="sxs-lookup"><span data-stu-id="cf2da-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cf2da-119">元素</span><span class="sxs-lookup"><span data-stu-id="cf2da-119">Element</span></span>|<span data-ttu-id="cf2da-120">描述</span><span class="sxs-lookup"><span data-stu-id="cf2da-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cf2da-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="cf2da-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="cf2da-122">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="cf2da-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="cf2da-123">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="cf2da-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="cf2da-124">包含 \<cryptographySettings> 項目。</span><span class="sxs-lookup"><span data-stu-id="cf2da-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cf2da-125">範例</span><span class="sxs-lookup"><span data-stu-id="cf2da-125">Example</span></span>  
 <span data-ttu-id="cf2da-126">下面的示例演示如何使用**\<加密NameMapping>** 元素來引用加密類並配置運行時。</span><span class="sxs-lookup"><span data-stu-id="cf2da-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="cf2da-127">然後，可以將字串"RSA"傳遞給 方法，<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>並使用 方法<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>返回物件`MyCryptoRSAClass`。</span><span class="sxs-lookup"><span data-stu-id="cf2da-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf2da-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf2da-128">See also</span></span>

- [<span data-ttu-id="cf2da-129">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="cf2da-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cf2da-130">加密設定架構</span><span class="sxs-lookup"><span data-stu-id="cf2da-130">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cf2da-131">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="cf2da-131">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="cf2da-132">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="cf2da-132">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

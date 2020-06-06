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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155215"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="69e96-102">\<cryptoNameMapping> 項目</span><span class="sxs-lookup"><span data-stu-id="69e96-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="69e96-103">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="69e96-103">Contains mappings of classes to friendly names.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**

## <a name="syntax"></a><span data-ttu-id="69e96-104">語法</span><span class="sxs-lookup"><span data-stu-id="69e96-104">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69e96-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="69e96-105">Attributes and Elements</span></span>  
 <span data-ttu-id="69e96-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="69e96-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69e96-107">屬性</span><span class="sxs-lookup"><span data-stu-id="69e96-107">Attributes</span></span>  
 <span data-ttu-id="69e96-108">無。</span><span class="sxs-lookup"><span data-stu-id="69e96-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="69e96-109">子元素</span><span class="sxs-lookup"><span data-stu-id="69e96-109">Child Elements</span></span>  
  
|<span data-ttu-id="69e96-110">元素</span><span class="sxs-lookup"><span data-stu-id="69e96-110">Element</span></span>|<span data-ttu-id="69e96-111">描述</span><span class="sxs-lookup"><span data-stu-id="69e96-111">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="69e96-112">包含在專案中有易記名稱對應的密碼編譯類別清單 **\<nameEntry>** 。</span><span class="sxs-lookup"><span data-stu-id="69e96-112">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="69e96-113">將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。</span><span class="sxs-lookup"><span data-stu-id="69e96-113">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69e96-114">父項目</span><span class="sxs-lookup"><span data-stu-id="69e96-114">Parent Elements</span></span>  
  
|<span data-ttu-id="69e96-115">元素</span><span class="sxs-lookup"><span data-stu-id="69e96-115">Element</span></span>|<span data-ttu-id="69e96-116">描述</span><span class="sxs-lookup"><span data-stu-id="69e96-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="69e96-117">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="69e96-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="69e96-118">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="69e96-118">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="69e96-119">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="69e96-119">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="69e96-120">包含 \<cryptographySettings> 元素。</span><span class="sxs-lookup"><span data-stu-id="69e96-120">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="69e96-121">範例</span><span class="sxs-lookup"><span data-stu-id="69e96-121">Example</span></span>  
 <span data-ttu-id="69e96-122">下列範例顯示如何使用專案 **\<cryptoNameMapping>** 來參考密碼編譯類別，以及設定執行時間。</span><span class="sxs-lookup"><span data-stu-id="69e96-122">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="69e96-123">接著，您可以將字串 "RSA" 傳遞給 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 方法，並使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法來傳回 `MyCryptoRSAClass` 物件。</span><span class="sxs-lookup"><span data-stu-id="69e96-123">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="69e96-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69e96-124">See also</span></span>

- [<span data-ttu-id="69e96-125">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="69e96-125">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="69e96-126">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="69e96-126">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="69e96-127">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="69e96-127">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="69e96-128">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="69e96-128">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

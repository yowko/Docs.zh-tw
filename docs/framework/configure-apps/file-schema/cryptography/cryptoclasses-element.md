---
title: <cryptoClasses> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: c93fadf51297d59ab499e25de283700364903049
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155242"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="4b4ab-102">\<cryptoClasses> 項目</span><span class="sxs-lookup"><span data-stu-id="4b4ab-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="4b4ab-103">包含在專案中有易記名稱對應的密碼編譯類別清單 [\<nameEntry>](nameentry-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="4b4ab-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**  
  
## <a name="syntax"></a><span data-ttu-id="4b4ab-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b4ab-104">Syntax</span></span>  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b4ab-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4b4ab-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4b4ab-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4b4ab-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b4ab-107">屬性</span><span class="sxs-lookup"><span data-stu-id="4b4ab-107">Attributes</span></span>  
 <span data-ttu-id="4b4ab-108">無。</span><span class="sxs-lookup"><span data-stu-id="4b4ab-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4b4ab-109">子元素</span><span class="sxs-lookup"><span data-stu-id="4b4ab-109">Child Elements</span></span>  
  
|<span data-ttu-id="4b4ab-110">元素</span><span class="sxs-lookup"><span data-stu-id="4b4ab-110">Element</span></span>|<span data-ttu-id="4b4ab-111">描述</span><span class="sxs-lookup"><span data-stu-id="4b4ab-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoClass>](cryptoclass-element.md)|<span data-ttu-id="4b4ab-112">包含在專案中具有易記名稱對應的密碼編譯類別 **\<nameEntry>** 。</span><span class="sxs-lookup"><span data-stu-id="4b4ab-112">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b4ab-113">父項目</span><span class="sxs-lookup"><span data-stu-id="4b4ab-113">Parent Elements</span></span>  
  
|<span data-ttu-id="4b4ab-114">元素</span><span class="sxs-lookup"><span data-stu-id="4b4ab-114">Element</span></span>|<span data-ttu-id="4b4ab-115">描述</span><span class="sxs-lookup"><span data-stu-id="4b4ab-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4b4ab-116">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="4b4ab-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="4b4ab-117">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="4b4ab-117">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="4b4ab-118">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="4b4ab-118">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="4b4ab-119">包含 `cryptographySettings` 元素。</span><span class="sxs-lookup"><span data-stu-id="4b4ab-119">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4b4ab-120">範例</span><span class="sxs-lookup"><span data-stu-id="4b4ab-120">Example</span></span>  
 <span data-ttu-id="4b4ab-121">下列範例示範如何使用 **\<cryptoClass>** 元素來參考密碼編譯類別，以及如何設定執行時間。</span><span class="sxs-lookup"><span data-stu-id="4b4ab-121">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="4b4ab-122">接著，您可以將字串 "RSA" 傳遞給 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 方法，並使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法來傳回 `MyCryptoRSAClass` 物件。</span><span class="sxs-lookup"><span data-stu-id="4b4ab-122">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b4ab-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b4ab-123">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="4b4ab-124">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="4b4ab-124">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4b4ab-125">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="4b4ab-125">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4b4ab-126">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="4b4ab-126">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="4b4ab-127">Cryptoconfig.createfromname. CreateFromName。</span><span class="sxs-lookup"><span data-stu-id="4b4ab-127">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="4b4ab-128">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="4b4ab-128">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

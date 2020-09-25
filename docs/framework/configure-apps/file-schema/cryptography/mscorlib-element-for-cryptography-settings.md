---
title: 密碼編譯設定的 <mscorlib> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: 1788205997d0dc49df172c9dfe48faceb8fc3290
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201781"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="bb1c3-102">密碼編譯設定的 \<mscorlib> 項目</span><span class="sxs-lookup"><span data-stu-id="bb1c3-102">\<mscorlib> Element for Cryptography Settings</span></span>

<span data-ttu-id="bb1c3-103">包含[ \<cryptographySettings> 元素](cryptographysettings-element.md)。</span><span class="sxs-lookup"><span data-stu-id="bb1c3-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<mscorlib>**  
  
## <a name="syntax"></a><span data-ttu-id="bb1c3-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="bb1c3-104">Syntax</span></span>  
  
```xml  
      <mscorlib>
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb1c3-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bb1c3-105">Attributes and Elements</span></span>  

 <span data-ttu-id="bb1c3-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bb1c3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb1c3-107">屬性</span><span class="sxs-lookup"><span data-stu-id="bb1c3-107">Attributes</span></span>  

 <span data-ttu-id="bb1c3-108">無。</span><span class="sxs-lookup"><span data-stu-id="bb1c3-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bb1c3-109">子元素</span><span class="sxs-lookup"><span data-stu-id="bb1c3-109">Child Elements</span></span>  
  
|<span data-ttu-id="bb1c3-110">項目</span><span class="sxs-lookup"><span data-stu-id="bb1c3-110">Element</span></span>|<span data-ttu-id="bb1c3-111">描述</span><span class="sxs-lookup"><span data-stu-id="bb1c3-111">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="bb1c3-112">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="bb1c3-112">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bb1c3-113">父項目</span><span class="sxs-lookup"><span data-stu-id="bb1c3-113">Parent Elements</span></span>  
  
|<span data-ttu-id="bb1c3-114">項目</span><span class="sxs-lookup"><span data-stu-id="bb1c3-114">Element</span></span>|<span data-ttu-id="bb1c3-115">描述</span><span class="sxs-lookup"><span data-stu-id="bb1c3-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bb1c3-116">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="bb1c3-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bb1c3-117">範例</span><span class="sxs-lookup"><span data-stu-id="bb1c3-117">Example</span></span>  

 <span data-ttu-id="bb1c3-118">下列範例示範如何使用專案 **\<mscorlib>** 來參考加密類別，以及如何設定執行時間。</span><span class="sxs-lookup"><span data-stu-id="bb1c3-118">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="bb1c3-119">然後，您可以將字串 "RSA" 傳遞給 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 方法，並使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法來傳回 `MyCryptoRSAClass` 物件。</span><span class="sxs-lookup"><span data-stu-id="bb1c3-119">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bb1c3-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb1c3-120">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="bb1c3-121">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="bb1c3-121">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bb1c3-122">密碼編譯設定架構</span><span class="sxs-lookup"><span data-stu-id="bb1c3-122">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bb1c3-123">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="bb1c3-123">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="bb1c3-124">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="bb1c3-124">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

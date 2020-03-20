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
ms.openlocfilehash: d1d805f7154c18dba2dcd4eb7228cc200d8da811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155177"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="cbba5-102">\<用於加密設定的 mscorlib>元素</span><span class="sxs-lookup"><span data-stu-id="cbba5-102">\<mscorlib> Element for Cryptography Settings</span></span>
<span data-ttu-id="cbba5-103">包含[\<加密設定>元素](cryptographysettings-element.md)。</span><span class="sxs-lookup"><span data-stu-id="cbba5-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[<span data-ttu-id="cbba5-104">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="cbba5-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="cbba5-105">&nbsp;&nbsp;**\<姆斯科利布>**</span><span class="sxs-lookup"><span data-stu-id="cbba5-105">&nbsp;&nbsp;**\<mscorlib>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbba5-106">語法</span><span class="sxs-lookup"><span data-stu-id="cbba5-106">Syntax</span></span>  
  
```xml  
      <mscorlib>
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbba5-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cbba5-107">Attributes and Elements</span></span>  
 <span data-ttu-id="cbba5-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cbba5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbba5-109">屬性</span><span class="sxs-lookup"><span data-stu-id="cbba5-109">Attributes</span></span>  
 <span data-ttu-id="cbba5-110">無。</span><span class="sxs-lookup"><span data-stu-id="cbba5-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cbba5-111">子元素</span><span class="sxs-lookup"><span data-stu-id="cbba5-111">Child Elements</span></span>  
  
|<span data-ttu-id="cbba5-112">元素</span><span class="sxs-lookup"><span data-stu-id="cbba5-112">Element</span></span>|<span data-ttu-id="cbba5-113">描述</span><span class="sxs-lookup"><span data-stu-id="cbba5-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="cbba5-114">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="cbba5-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cbba5-115">父項目</span><span class="sxs-lookup"><span data-stu-id="cbba5-115">Parent Elements</span></span>  
  
|<span data-ttu-id="cbba5-116">元素</span><span class="sxs-lookup"><span data-stu-id="cbba5-116">Element</span></span>|<span data-ttu-id="cbba5-117">描述</span><span class="sxs-lookup"><span data-stu-id="cbba5-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cbba5-118">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="cbba5-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cbba5-119">範例</span><span class="sxs-lookup"><span data-stu-id="cbba5-119">Example</span></span>  
 <span data-ttu-id="cbba5-120">下面的示例演示如何使用**\<mscorlib>** 元素來引用加密類並配置運行時。</span><span class="sxs-lookup"><span data-stu-id="cbba5-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="cbba5-121">然後，可以將字串"RSA"傳遞給 方法，<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>並使用 方法<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>返回物件`MyCryptoRSAClass`。</span><span class="sxs-lookup"><span data-stu-id="cbba5-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cbba5-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbba5-122">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="cbba5-123">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="cbba5-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cbba5-124">加密設定架構</span><span class="sxs-lookup"><span data-stu-id="cbba5-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cbba5-125">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="cbba5-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="cbba5-126">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="cbba5-126">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

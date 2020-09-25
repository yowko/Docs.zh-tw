---
title: <nameEntry> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: 4341b1fcd3762e5aa55f0ba988f7f49d4b5cacd6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201768"
---
# <a name="nameentry-element"></a><span data-ttu-id="275eb-102">\<nameEntry> 項目</span><span class="sxs-lookup"><span data-stu-id="275eb-102">\<nameEntry> Element</span></span>

<span data-ttu-id="275eb-103">將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。</span><span class="sxs-lookup"><span data-stu-id="275eb-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameEntry>**  
  
## <a name="syntax"></a><span data-ttu-id="275eb-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="275eb-104">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="275eb-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="275eb-105">Attributes and Elements</span></span>  

 <span data-ttu-id="275eb-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="275eb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="275eb-107">屬性</span><span class="sxs-lookup"><span data-stu-id="275eb-107">Attributes</span></span>  
  
|<span data-ttu-id="275eb-108">屬性</span><span class="sxs-lookup"><span data-stu-id="275eb-108">Attribute</span></span>|<span data-ttu-id="275eb-109">描述</span><span class="sxs-lookup"><span data-stu-id="275eb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="275eb-110">**name**</span><span class="sxs-lookup"><span data-stu-id="275eb-110">**name**</span></span>|<span data-ttu-id="275eb-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="275eb-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="275eb-112">指定密碼編譯類別所實行之演算法的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="275eb-112">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="275eb-113">**class**</span><span class="sxs-lookup"><span data-stu-id="275eb-113">**class**</span></span>|<span data-ttu-id="275eb-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="275eb-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="275eb-115">在元素中指定 **name** 屬性的值 [\<cryptoClass>](cryptoclass-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="275eb-115">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="275eb-116">子元素</span><span class="sxs-lookup"><span data-stu-id="275eb-116">Child Elements</span></span>  

 <span data-ttu-id="275eb-117">無。</span><span class="sxs-lookup"><span data-stu-id="275eb-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="275eb-118">父項目</span><span class="sxs-lookup"><span data-stu-id="275eb-118">Parent Elements</span></span>  
  
|<span data-ttu-id="275eb-119">項目</span><span class="sxs-lookup"><span data-stu-id="275eb-119">Element</span></span>|<span data-ttu-id="275eb-120">描述</span><span class="sxs-lookup"><span data-stu-id="275eb-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="275eb-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="275eb-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="275eb-122">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="275eb-122">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="275eb-123">備註</span><span class="sxs-lookup"><span data-stu-id="275eb-123">Remarks</span></span>  

 <span data-ttu-id="275eb-124">**Name**屬性可以是在命名空間中找到的其中一個抽象類別的名稱 <xref:System.Security.Cryptography> 。</span><span class="sxs-lookup"><span data-stu-id="275eb-124">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="275eb-125">當您在抽象密碼編譯類別上呼叫 **Create** 方法時，抽象類別名稱會傳遞給 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="275eb-125">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="275eb-126">**CreateFromName** 會傳回 **類別** 屬性所表示之型別的實例。</span><span class="sxs-lookup"><span data-stu-id="275eb-126">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="275eb-127">如果 **name** 屬性是簡短名稱，例如 RSA，則在呼叫 **CreateFromName** 方法時，您可以使用該名稱。</span><span class="sxs-lookup"><span data-stu-id="275eb-127">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="275eb-128">範例</span><span class="sxs-lookup"><span data-stu-id="275eb-128">Example</span></span>  

 <span data-ttu-id="275eb-129">下列範例示範如何使用專案 **\<nameEntry>** 來參考加密類別，以及如何設定執行時間。</span><span class="sxs-lookup"><span data-stu-id="275eb-129">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="275eb-130">然後，您可以將字串 "RSA" 傳遞給 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 方法，並使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法來傳回 `MyCryptoRSAClass` 物件。</span><span class="sxs-lookup"><span data-stu-id="275eb-130">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="275eb-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="275eb-131">See also</span></span>

- [<span data-ttu-id="275eb-132">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="275eb-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="275eb-133">密碼編譯設定架構</span><span class="sxs-lookup"><span data-stu-id="275eb-133">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="275eb-134">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="275eb-134">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="275eb-135">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="275eb-135">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

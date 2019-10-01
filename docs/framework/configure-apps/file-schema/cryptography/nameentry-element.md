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
ms.openlocfilehash: a339638587f8b544bbc1b0073553f6232ce09694
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699785"
---
# <a name="nameentry-element"></a><span data-ttu-id="67691-102">@no__t 0nameEntry > 元素</span><span class="sxs-lookup"><span data-stu-id="67691-102">\<nameEntry> Element</span></span>
<span data-ttu-id="67691-103">將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。</span><span class="sxs-lookup"><span data-stu-id="67691-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
[<span data-ttu-id="67691-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="67691-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="67691-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="67691-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="67691-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="67691-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="67691-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="67691-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="67691-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="67691-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameEntry>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67691-109">語法</span><span class="sxs-lookup"><span data-stu-id="67691-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67691-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="67691-110">Attributes and Elements</span></span>  
 <span data-ttu-id="67691-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="67691-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67691-112">屬性</span><span class="sxs-lookup"><span data-stu-id="67691-112">Attributes</span></span>  
  
|<span data-ttu-id="67691-113">屬性</span><span class="sxs-lookup"><span data-stu-id="67691-113">Attribute</span></span>|<span data-ttu-id="67691-114">描述</span><span class="sxs-lookup"><span data-stu-id="67691-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67691-115">**name**</span><span class="sxs-lookup"><span data-stu-id="67691-115">**name**</span></span>|<span data-ttu-id="67691-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="67691-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="67691-117">指定密碼編譯類別所實行之演算法的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="67691-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="67691-118">**class**</span><span class="sxs-lookup"><span data-stu-id="67691-118">**class**</span></span>|<span data-ttu-id="67691-119">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="67691-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="67691-120">指定[@no__t 2cryptoClass >](cryptoclass-element.md)元素中**name**屬性的值。</span><span class="sxs-lookup"><span data-stu-id="67691-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67691-121">子元素</span><span class="sxs-lookup"><span data-stu-id="67691-121">Child Elements</span></span>  
 <span data-ttu-id="67691-122">無。</span><span class="sxs-lookup"><span data-stu-id="67691-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67691-123">父項目</span><span class="sxs-lookup"><span data-stu-id="67691-123">Parent Elements</span></span>  
  
|<span data-ttu-id="67691-124">項目</span><span class="sxs-lookup"><span data-stu-id="67691-124">Element</span></span>|<span data-ttu-id="67691-125">描述</span><span class="sxs-lookup"><span data-stu-id="67691-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="67691-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="67691-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="67691-127">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="67691-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67691-128">備註</span><span class="sxs-lookup"><span data-stu-id="67691-128">Remarks</span></span>  
 <span data-ttu-id="67691-129">**Name**屬性可以是在 @no__t 1 命名空間中找到的其中一個抽象類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="67691-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="67691-130">當您在抽象密碼編譯類別上呼叫**Create**方法時，會將抽象類別名稱傳遞給 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="67691-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="67691-131">**CreateFromName**會傳回**類別**屬性所指示之類型的實例。</span><span class="sxs-lookup"><span data-stu-id="67691-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="67691-132">如果**name**屬性是簡短名稱（例如 RSA），您可以在呼叫**CreateFromName**方法時使用該名稱。</span><span class="sxs-lookup"><span data-stu-id="67691-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67691-133">範例</span><span class="sxs-lookup"><span data-stu-id="67691-133">Example</span></span>  
 <span data-ttu-id="67691-134">下列範例示範如何使用 **@no__t 1nameEntry 的 >** 專案來參考密碼編譯類別，並設定執行時間。</span><span class="sxs-lookup"><span data-stu-id="67691-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="67691-135">接著，您可以將字串 "RSA" 傳遞給 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 方法，然後使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法傳回 @no__t 2 物件。</span><span class="sxs-lookup"><span data-stu-id="67691-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="67691-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67691-136">See also</span></span>

- [<span data-ttu-id="67691-137">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="67691-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="67691-138">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="67691-138">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="67691-139">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="67691-139">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="67691-140">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="67691-140">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

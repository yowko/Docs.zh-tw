---
title: 密碼編譯設定結構描述
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: 474c3274bfba6803ebb17289f138251d755250e4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699808"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="f2b42-102">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f2b42-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="f2b42-103">密碼編譯設定結構描述包含指定如何將易記的演算法名稱對應至實作密碼編譯演算法之類別的項目。</span><span class="sxs-lookup"><span data-stu-id="f2b42-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
[<span data-ttu-id="f2b42-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="f2b42-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="f2b42-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f2b42-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="f2b42-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2b42-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="f2b42-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2b42-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="f2b42-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0cryptoClasses >** ](cryptoclasses-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2b42-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)</span></span>  
<span data-ttu-id="f2b42-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9[ **&nbsp;2cryptoClass >** ](cryptoclass-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2b42-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)</span></span>  
<span data-ttu-id="f2b42-110">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0nameEntry >** ](nameentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2b42-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)</span></span>  
<span data-ttu-id="f2b42-111">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<oidMap >** ](oidmap-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2b42-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)</span></span>  
<span data-ttu-id="f2b42-112">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6[ **\<oidEntry >** ](oidentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2b42-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)</span></span>  
  
|<span data-ttu-id="f2b42-113">元素</span><span class="sxs-lookup"><span data-stu-id="f2b42-113">Element</span></span>|<span data-ttu-id="f2b42-114">描述</span><span class="sxs-lookup"><span data-stu-id="f2b42-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2b42-115"> **\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="f2b42-115">**\<cryptoClasses**></span></span>](cryptoclasses-element.md)|<span data-ttu-id="f2b42-116">包含密碼編譯類別清單，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="f2b42-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="f2b42-117"> **\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="f2b42-117">**\<cryptoClass**></span></span>](cryptoclass-element.md)|<span data-ttu-id="f2b42-118">包含密碼編譯類別，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="f2b42-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="f2b42-119"> **\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="f2b42-119">**\<cryptographySettings**></span></span>](cryptographysettings-element.md)|<span data-ttu-id="f2b42-120">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="f2b42-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="f2b42-121"> **\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="f2b42-121">**\<cryptoNameMapping**></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="f2b42-122">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="f2b42-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="f2b42-123">密碼編譯設定的 **\<mscorlib>** 項目</span><span class="sxs-lookup"><span data-stu-id="f2b42-123">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="f2b42-124">包含 **\<cryptographySettings>** 項目。</span><span class="sxs-lookup"><span data-stu-id="f2b42-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="f2b42-125"> **\<nameEntry>** </span><span class="sxs-lookup"><span data-stu-id="f2b42-125">**\<nameEntry>**</span></span>](nameentry-element.md)|<span data-ttu-id="f2b42-126">將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。</span><span class="sxs-lookup"><span data-stu-id="f2b42-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="f2b42-127"> **\<oidEntry>** </span><span class="sxs-lookup"><span data-stu-id="f2b42-127">**\<oidEntry>**</span></span>](oidentry-element.md)|<span data-ttu-id="f2b42-128">將 ASN.1 物件識別碼 (OID) 對應至易記名稱。</span><span class="sxs-lookup"><span data-stu-id="f2b42-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="f2b42-129"> **\<oidMap>** </span><span class="sxs-lookup"><span data-stu-id="f2b42-129">**\<oidMap>**</span></span>](oidmap-element.md)|<span data-ttu-id="f2b42-130">包含類別的 ASN.1 OID 對應。</span><span class="sxs-lookup"><span data-stu-id="f2b42-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2b42-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2b42-131">See also</span></span>

- [<span data-ttu-id="f2b42-132">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="f2b42-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f2b42-133">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="f2b42-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)

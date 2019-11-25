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
ms.openlocfilehash: c632a15552c8ba5743aac1309098b7d7ef949bbd
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087998"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="8b0b6-102">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="8b0b6-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="8b0b6-103">密碼編譯設定結構描述包含指定如何將易記的演算法名稱對應至實作密碼編譯演算法之類別的項目。</span><span class="sxs-lookup"><span data-stu-id="8b0b6-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
<span data-ttu-id="8b0b6-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8b0b6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8b0b6-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8b0b6-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="8b0b6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="8b0b6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="8b0b6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="8b0b6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>\
<span data-ttu-id="8b0b6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoClasses >** ](cryptoclasses-element.md)</span><span class="sxs-lookup"><span data-stu-id="8b0b6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)</span></span>\
<span data-ttu-id="8b0b6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoClass >** ](cryptoclass-element.md)</span><span class="sxs-lookup"><span data-stu-id="8b0b6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)</span></span>\
<span data-ttu-id="8b0b6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<y >** ](nameentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="8b0b6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)</span></span>\
<span data-ttu-id="8b0b6-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<oidMap >** ](oidmap-element.md)</span><span class="sxs-lookup"><span data-stu-id="8b0b6-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)</span></span>\
<span data-ttu-id="8b0b6-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<y >** ](oidentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="8b0b6-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)</span></span>

|<span data-ttu-id="8b0b6-113">項目</span><span class="sxs-lookup"><span data-stu-id="8b0b6-113">Element</span></span>|<span data-ttu-id="8b0b6-114">描述</span><span class="sxs-lookup"><span data-stu-id="8b0b6-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b0b6-115"> **\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="8b0b6-115">**\<cryptoClasses**></span></span>](cryptoclasses-element.md)|<span data-ttu-id="8b0b6-116">包含密碼編譯類別清單，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="8b0b6-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="8b0b6-117"> **\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="8b0b6-117">**\<cryptoClass**></span></span>](cryptoclass-element.md)|<span data-ttu-id="8b0b6-118">包含密碼編譯類別，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="8b0b6-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="8b0b6-119"> **\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="8b0b6-119">**\<cryptographySettings**></span></span>](cryptographysettings-element.md)|<span data-ttu-id="8b0b6-120">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="8b0b6-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="8b0b6-121"> **\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="8b0b6-121">**\<cryptoNameMapping**></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="8b0b6-122">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="8b0b6-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="8b0b6-123">密碼編譯設定的 **\<mscorlib>** 項目</span><span class="sxs-lookup"><span data-stu-id="8b0b6-123">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="8b0b6-124">包含 **\<cryptographySettings>** 項目。</span><span class="sxs-lookup"><span data-stu-id="8b0b6-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="8b0b6-125"> **\<nameEntry>** </span><span class="sxs-lookup"><span data-stu-id="8b0b6-125">**\<nameEntry>**</span></span>](nameentry-element.md)|<span data-ttu-id="8b0b6-126">將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。</span><span class="sxs-lookup"><span data-stu-id="8b0b6-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="8b0b6-127"> **\<oidEntry>** </span><span class="sxs-lookup"><span data-stu-id="8b0b6-127">**\<oidEntry>**</span></span>](oidentry-element.md)|<span data-ttu-id="8b0b6-128">將 ASN.1 物件識別碼 (OID) 對應至易記名稱。</span><span class="sxs-lookup"><span data-stu-id="8b0b6-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="8b0b6-129"> **\<oidMap>** </span><span class="sxs-lookup"><span data-stu-id="8b0b6-129">**\<oidMap>**</span></span>](oidmap-element.md)|<span data-ttu-id="8b0b6-130">包含類別的 ASN.1 OID 對應。</span><span class="sxs-lookup"><span data-stu-id="8b0b6-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b0b6-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="8b0b6-131">See also</span></span>

- [<span data-ttu-id="8b0b6-132">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="8b0b6-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="8b0b6-133">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="8b0b6-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)

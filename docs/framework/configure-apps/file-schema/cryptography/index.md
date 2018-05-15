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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b7f41bc477f8d8095bf73859c02b7e2fc2443c14
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="84474-102">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="84474-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="84474-103">密碼編譯設定結構描述包含指定如何將易記的演算法名稱對應至實作密碼編譯演算法之類別的項目。</span><span class="sxs-lookup"><span data-stu-id="84474-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="84474-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="84474-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="84474-105">**\<mscorlib>**</span><span class="sxs-lookup"><span data-stu-id="84474-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="84474-106">**\<cryptographySettings>**</span><span class="sxs-lookup"><span data-stu-id="84474-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="84474-107">**\<cryptoNameMapping>**</span><span class="sxs-lookup"><span data-stu-id="84474-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="84474-108">**\<cryptoClasses>**</span><span class="sxs-lookup"><span data-stu-id="84474-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="84474-109">**\<cryptoClass>**</span><span class="sxs-lookup"><span data-stu-id="84474-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="84474-110">**\<nameEntry>**</span><span class="sxs-lookup"><span data-stu-id="84474-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="84474-111">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="84474-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="84474-112">**\<oidEntry>**</span><span class="sxs-lookup"><span data-stu-id="84474-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="84474-113">項目</span><span class="sxs-lookup"><span data-stu-id="84474-113">Element</span></span>|<span data-ttu-id="84474-114">描述</span><span class="sxs-lookup"><span data-stu-id="84474-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84474-115">**\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="84474-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="84474-116">包含密碼編譯類別清單，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="84474-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="84474-117">**\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="84474-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="84474-118">包含密碼編譯類別，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="84474-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="84474-119">**\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="84474-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="84474-120">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="84474-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="84474-121">**\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="84474-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="84474-122">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="84474-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="84474-123">密碼編譯設定的 **\<mscorlib>** 項目</span><span class="sxs-lookup"><span data-stu-id="84474-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="84474-124">包含 **\<cryptographySettings>** 項目。</span><span class="sxs-lookup"><span data-stu-id="84474-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="84474-125">**\<nameEntry>**</span><span class="sxs-lookup"><span data-stu-id="84474-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="84474-126">將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。</span><span class="sxs-lookup"><span data-stu-id="84474-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="84474-127">**\<oidEntry>**</span><span class="sxs-lookup"><span data-stu-id="84474-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="84474-128">將 ASN.1 物件識別碼 (OID) 對應至易記名稱。</span><span class="sxs-lookup"><span data-stu-id="84474-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="84474-129">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="84474-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="84474-130">包含類別的 ASN.1 OID 對應。</span><span class="sxs-lookup"><span data-stu-id="84474-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84474-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84474-131">See Also</span></span>  
 [<span data-ttu-id="84474-132">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="84474-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="84474-133">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="84474-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)

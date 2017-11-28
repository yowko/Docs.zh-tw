---
title: "密碼編譯設定結構描述"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c7d1e193236528c96e8253668c742883090ae188
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="89a2a-102">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="89a2a-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="89a2a-103">密碼編譯設定結構描述包含指定如何將易記的演算法名稱對應至實作密碼編譯演算法之類別的項目。</span><span class="sxs-lookup"><span data-stu-id="89a2a-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="89a2a-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="89a2a-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="89a2a-105">**\<mscorlib>**</span><span class="sxs-lookup"><span data-stu-id="89a2a-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="89a2a-106">**\<cryptographySettings>**</span><span class="sxs-lookup"><span data-stu-id="89a2a-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="89a2a-107">**\<cryptoNameMapping>**</span><span class="sxs-lookup"><span data-stu-id="89a2a-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="89a2a-108">**\<cryptoClasses>**</span><span class="sxs-lookup"><span data-stu-id="89a2a-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="89a2a-109">**\<cryptoClass>**</span><span class="sxs-lookup"><span data-stu-id="89a2a-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="89a2a-110">**\<nameEntry>**</span><span class="sxs-lookup"><span data-stu-id="89a2a-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="89a2a-111">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="89a2a-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="89a2a-112">**\<oidEntry>**</span><span class="sxs-lookup"><span data-stu-id="89a2a-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="89a2a-113">項目</span><span class="sxs-lookup"><span data-stu-id="89a2a-113">Element</span></span>|<span data-ttu-id="89a2a-114">說明</span><span class="sxs-lookup"><span data-stu-id="89a2a-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89a2a-115">**\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="89a2a-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="89a2a-116">包含密碼編譯類別清單，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="89a2a-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="89a2a-117">**\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="89a2a-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="89a2a-118">包含密碼編譯類別，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="89a2a-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="89a2a-119">**\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="89a2a-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="89a2a-120">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="89a2a-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="89a2a-121">**\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="89a2a-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="89a2a-122">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="89a2a-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="89a2a-123">密碼編譯設定的 **\<mscorlib>** 項目</span><span class="sxs-lookup"><span data-stu-id="89a2a-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="89a2a-124">包含 **\<cryptographySettings>** 項目。</span><span class="sxs-lookup"><span data-stu-id="89a2a-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="89a2a-125">**\<nameEntry>**</span><span class="sxs-lookup"><span data-stu-id="89a2a-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="89a2a-126">將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。</span><span class="sxs-lookup"><span data-stu-id="89a2a-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="89a2a-127">**\<oidEntry>**</span><span class="sxs-lookup"><span data-stu-id="89a2a-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="89a2a-128">將 ASN.1 物件識別碼 (OID) 對應至易記名稱。</span><span class="sxs-lookup"><span data-stu-id="89a2a-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="89a2a-129">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="89a2a-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="89a2a-130">包含類別的 ASN.1 OID 對應。</span><span class="sxs-lookup"><span data-stu-id="89a2a-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89a2a-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89a2a-131">See Also</span></span>  
 [<span data-ttu-id="89a2a-132">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="89a2a-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="89a2a-133">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="89a2a-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)

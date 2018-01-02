---
title: "&lt;assemblyBinding&gt;元素&lt;組態&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8d670c56a885a5fdae059a87f63fba9ab32f020c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="73567-102">\<assemblyBinding > 項目\<設定 ></span><span class="sxs-lookup"><span data-stu-id="73567-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="73567-103">指定位於組態層級的組件繫結原則。</span><span class="sxs-lookup"><span data-stu-id="73567-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="73567-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="73567-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="73567-105">&nbsp;&nbsp;**\<assemblyBinding >**</span><span class="sxs-lookup"><span data-stu-id="73567-105">&nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="73567-106">語法</span><span class="sxs-lookup"><span data-stu-id="73567-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="73567-107">屬性</span><span class="sxs-lookup"><span data-stu-id="73567-107">Attribute</span></span>

|           | <span data-ttu-id="73567-108">描述</span><span class="sxs-lookup"><span data-stu-id="73567-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="73567-109">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="73567-109">**xmlns**</span></span> | <span data-ttu-id="73567-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="73567-110">Required attribute.</span></span><br><br><span data-ttu-id="73567-111">指定組件繫結所需的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="73567-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="73567-112">使用字串 "urn:schemas-microsoft-com:asm.v1" 做為值。</span><span class="sxs-lookup"><span data-stu-id="73567-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="73567-113">父項目</span><span class="sxs-lookup"><span data-stu-id="73567-113">Parent element</span></span>

|     | <span data-ttu-id="73567-114">描述</span><span class="sxs-lookup"><span data-stu-id="73567-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="73567-115">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="73567-115">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="73567-116">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="73567-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="73567-117">子元素</span><span class="sxs-lookup"><span data-stu-id="73567-117">Child element</span></span>

|     | <span data-ttu-id="73567-118">描述</span><span class="sxs-lookup"><span data-stu-id="73567-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="73567-119">**\<linkedConfiguration >**</span><span class="sxs-lookup"><span data-stu-id="73567-119">**\<linkedConfiguration>**</span></span>](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | <span data-ttu-id="73567-120">指定要包含的組態檔。</span><span class="sxs-lookup"><span data-stu-id="73567-120">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="73567-121">備註</span><span class="sxs-lookup"><span data-stu-id="73567-121">Remarks</span></span>

<span data-ttu-id="73567-122">[  **\<LinkedConfiguration >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md)項目可簡化管理的元件組件，藉由使用應用程式組態檔，以包含組件中的組態檔已知的位置，而不是複製的組件組態設定。</span><span class="sxs-lookup"><span data-stu-id="73567-122">The [**\<linkedConfiguration>**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="73567-123"> **\<LinkedConfiguration >**項目不支援有 Windows-並存資訊清單的應用程式。</span><span class="sxs-lookup"><span data-stu-id="73567-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="73567-124">範例</span><span class="sxs-lookup"><span data-stu-id="73567-124">Example</span></span>

<span data-ttu-id="73567-125">下列範例會示範如何包含在本機硬碟上的組態檔：</span><span class="sxs-lookup"><span data-stu-id="73567-125">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="73567-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73567-126">See also</span></span>

[<span data-ttu-id="73567-127">適用於.NET Framework 組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="73567-127">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)

---
title: '&lt;assemblyBinding&gt;項目&lt;組態&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 5693b92ac35a357ff1f8643d0eb9ec2105acecb4
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47073459"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="75827-102">\<Assemblybinding> > 項目\<設定 ></span><span class="sxs-lookup"><span data-stu-id="75827-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="75827-103">指定位於組態層級的組件繫結原則。</span><span class="sxs-lookup"><span data-stu-id="75827-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="75827-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="75827-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="75827-105">&nbsp;&nbsp;**\<Assemblybinding> >**</span><span class="sxs-lookup"><span data-stu-id="75827-105">&nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="75827-106">語法</span><span class="sxs-lookup"><span data-stu-id="75827-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="75827-107">屬性</span><span class="sxs-lookup"><span data-stu-id="75827-107">Attribute</span></span>

|           | <span data-ttu-id="75827-108">描述</span><span class="sxs-lookup"><span data-stu-id="75827-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="75827-109">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="75827-109">**xmlns**</span></span> | <span data-ttu-id="75827-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="75827-110">Required attribute.</span></span><br><br><span data-ttu-id="75827-111">指定組件繫結所需的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="75827-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="75827-112">使用字串 "urn:schemas-microsoft-com:asm.v1" 做為值。</span><span class="sxs-lookup"><span data-stu-id="75827-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="75827-113">父項目</span><span class="sxs-lookup"><span data-stu-id="75827-113">Parent element</span></span>

|     | <span data-ttu-id="75827-114">描述</span><span class="sxs-lookup"><span data-stu-id="75827-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="75827-115">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="75827-115">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="75827-116">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="75827-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="75827-117">子項目</span><span class="sxs-lookup"><span data-stu-id="75827-117">Child element</span></span>

|     | <span data-ttu-id="75827-118">描述</span><span class="sxs-lookup"><span data-stu-id="75827-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="75827-119">**\<linkedConfiguration >**</span><span class="sxs-lookup"><span data-stu-id="75827-119">**\<linkedConfiguration>**</span></span>](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | <span data-ttu-id="75827-120">指定要包含的組態檔。</span><span class="sxs-lookup"><span data-stu-id="75827-120">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="75827-121">備註</span><span class="sxs-lookup"><span data-stu-id="75827-121">Remarks</span></span>

<span data-ttu-id="75827-122">[  **\<LinkedConfiguration >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md)項目可簡化管理的元件組件，允許應用程式組態檔，以包含組件中的設定檔已知的位置，而不是複製的組件組態設定。</span><span class="sxs-lookup"><span data-stu-id="75827-122">The [**\<linkedConfiguration>**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="75827-123">**\<LinkedConfiguration >** 與 Windows 並排顯示的資訊清單的應用程式不支援項目。</span><span class="sxs-lookup"><span data-stu-id="75827-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="75827-124">範例</span><span class="sxs-lookup"><span data-stu-id="75827-124">Example</span></span>

<span data-ttu-id="75827-125">下列範例示範如何包含在本機硬碟上的組態檔：</span><span class="sxs-lookup"><span data-stu-id="75827-125">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="75827-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75827-126">See also</span></span>

[<span data-ttu-id="75827-127">適用於.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="75827-127">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)

---
title: <configuration> 的 <assemblyBinding> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: f5992a6085c32d37f56319cf8b2c361542c441e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674827"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="176ce-102">\<Assemblybinding> > 項目\<設定 ></span><span class="sxs-lookup"><span data-stu-id="176ce-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="176ce-103">指定位於組態層級的組件繫結原則。</span><span class="sxs-lookup"><span data-stu-id="176ce-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="176ce-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="176ce-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="176ce-105">&nbsp;&nbsp; **\<assemblyBinding>**</span><span class="sxs-lookup"><span data-stu-id="176ce-105">&nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="176ce-106">語法</span><span class="sxs-lookup"><span data-stu-id="176ce-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="176ce-107">屬性</span><span class="sxs-lookup"><span data-stu-id="176ce-107">Attribute</span></span>

|           | <span data-ttu-id="176ce-108">描述</span><span class="sxs-lookup"><span data-stu-id="176ce-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="176ce-109">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="176ce-109">**xmlns**</span></span> | <span data-ttu-id="176ce-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="176ce-110">Required attribute.</span></span><br><br><span data-ttu-id="176ce-111">指定組件繫結所需的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="176ce-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="176ce-112">使用字串 "urn:schemas-microsoft-com:asm.v1" 做為值。</span><span class="sxs-lookup"><span data-stu-id="176ce-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="176ce-113">父項目</span><span class="sxs-lookup"><span data-stu-id="176ce-113">Parent element</span></span>

|     | <span data-ttu-id="176ce-114">描述</span><span class="sxs-lookup"><span data-stu-id="176ce-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="176ce-115"> *\*\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="176ce-115">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="176ce-116">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="176ce-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="176ce-117">子項目</span><span class="sxs-lookup"><span data-stu-id="176ce-117">Child element</span></span>

|     | <span data-ttu-id="176ce-118">描述</span><span class="sxs-lookup"><span data-stu-id="176ce-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="176ce-119"> *\*\<linkedConfiguration>** </span><span class="sxs-lookup"><span data-stu-id="176ce-119">**\<linkedConfiguration>**</span></span>](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | <span data-ttu-id="176ce-120">指定要包含的組態檔。</span><span class="sxs-lookup"><span data-stu-id="176ce-120">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="176ce-121">備註</span><span class="sxs-lookup"><span data-stu-id="176ce-121">Remarks</span></span>

<span data-ttu-id="176ce-122">[  **\<LinkedConfiguration >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md)項目可簡化管理的元件組件，允許應用程式組態檔，以包含組件中的設定檔已知的位置，而不是複製的組件組態設定。</span><span class="sxs-lookup"><span data-stu-id="176ce-122">The [**\<linkedConfiguration>**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="176ce-123">**\<LinkedConfiguration >** 與 Windows 並排顯示的資訊清單的應用程式不支援項目。</span><span class="sxs-lookup"><span data-stu-id="176ce-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="176ce-124">範例</span><span class="sxs-lookup"><span data-stu-id="176ce-124">Example</span></span>

<span data-ttu-id="176ce-125">下列範例示範如何包含在本機硬碟上的組態檔：</span><span class="sxs-lookup"><span data-stu-id="176ce-125">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="176ce-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="176ce-126">See also</span></span>

- [<span data-ttu-id="176ce-127">適用於.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="176ce-127">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)

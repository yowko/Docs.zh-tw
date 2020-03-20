---
title: <configuration> 的 <assemblyBinding> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 21cf5e749b0dae310c3326f8abf82c6678fc97e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155475"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="17f16-102">\<用於\<配置>的程式集綁定>元素</span><span class="sxs-lookup"><span data-stu-id="17f16-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="17f16-103">指定位於組態層級的組件繫結原則。</span><span class="sxs-lookup"><span data-stu-id="17f16-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="17f16-104">&nbsp; [\*\* \<配置>\*\*](configuration-element.md)&nbsp;**程式集綁定>\<**</span><span class="sxs-lookup"><span data-stu-id="17f16-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="17f16-105">語法</span><span class="sxs-lookup"><span data-stu-id="17f16-105">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="17f16-106">屬性</span><span class="sxs-lookup"><span data-stu-id="17f16-106">Attribute</span></span>

|           | <span data-ttu-id="17f16-107">描述</span><span class="sxs-lookup"><span data-stu-id="17f16-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="17f16-108">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="17f16-108">**xmlns**</span></span> | <span data-ttu-id="17f16-109">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="17f16-109">Required attribute.</span></span><br><br><span data-ttu-id="17f16-110">指定組件繫結所需的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="17f16-110">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="17f16-111">使用字串 "urn:schemas-microsoft-com:asm.v1" 做為值。</span><span class="sxs-lookup"><span data-stu-id="17f16-111">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="17f16-112">父元素</span><span class="sxs-lookup"><span data-stu-id="17f16-112">Parent element</span></span>

|     | <span data-ttu-id="17f16-113">描述</span><span class="sxs-lookup"><span data-stu-id="17f16-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="17f16-114">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="17f16-114">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="17f16-115">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="17f16-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="17f16-116">子項目</span><span class="sxs-lookup"><span data-stu-id="17f16-116">Child element</span></span>

|     | <span data-ttu-id="17f16-117">描述</span><span class="sxs-lookup"><span data-stu-id="17f16-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="17f16-118">**\<連結配置>**</span><span class="sxs-lookup"><span data-stu-id="17f16-118">**\<linkedConfiguration>**</span></span>](linkedconfiguration-element.md) | <span data-ttu-id="17f16-119">指定要包含的組態檔。</span><span class="sxs-lookup"><span data-stu-id="17f16-119">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="17f16-120">備註</span><span class="sxs-lookup"><span data-stu-id="17f16-120">Remarks</span></span>

<span data-ttu-id="17f16-121">[\*\* \<連結配置>\*\*](linkedconfiguration-element.md)元素允許應用程式佈建檔在已知位置包含程式集設定檔，而不是複製程式集配置設置，從而簡化了元件程式集的管理。</span><span class="sxs-lookup"><span data-stu-id="17f16-121">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="17f16-122">對於具有 Windows 並行清單的應用程式，不支援**\<連結的配置>** 元素。</span><span class="sxs-lookup"><span data-stu-id="17f16-122">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="17f16-123">範例</span><span class="sxs-lookup"><span data-stu-id="17f16-123">Example</span></span>

<span data-ttu-id="17f16-124">下面的示例演示如何在本地硬碟上包含設定檔：</span><span class="sxs-lookup"><span data-stu-id="17f16-124">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="17f16-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17f16-125">See also</span></span>

- [<span data-ttu-id="17f16-126">.NET 框架的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="17f16-126">Configuration file schema for the .NET Framework</span></span>](index.md)

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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155475"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="b12bc-102">\<configuration> 的 \<assemblyBinding> 項目</span><span class="sxs-lookup"><span data-stu-id="b12bc-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="b12bc-103">指定位於組態層級的組件繫結原則。</span><span class="sxs-lookup"><span data-stu-id="b12bc-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="b12bc-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span><span class="sxs-lookup"><span data-stu-id="b12bc-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b12bc-105">語法</span><span class="sxs-lookup"><span data-stu-id="b12bc-105">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="b12bc-106">屬性</span><span class="sxs-lookup"><span data-stu-id="b12bc-106">Attribute</span></span>

|           | <span data-ttu-id="b12bc-107">描述</span><span class="sxs-lookup"><span data-stu-id="b12bc-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="b12bc-108">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="b12bc-108">**xmlns**</span></span> | <span data-ttu-id="b12bc-109">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="b12bc-109">Required attribute.</span></span><br><br><span data-ttu-id="b12bc-110">指定組件繫結所需的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="b12bc-110">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="b12bc-111">使用字串 "urn:schemas-microsoft-com:asm.v1" 做為值。</span><span class="sxs-lookup"><span data-stu-id="b12bc-111">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="b12bc-112">父元素</span><span class="sxs-lookup"><span data-stu-id="b12bc-112">Parent element</span></span>

|     | <span data-ttu-id="b12bc-113">描述</span><span class="sxs-lookup"><span data-stu-id="b12bc-113">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="b12bc-114">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="b12bc-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="b12bc-115">子項目</span><span class="sxs-lookup"><span data-stu-id="b12bc-115">Child element</span></span>

|     | <span data-ttu-id="b12bc-116">描述</span><span class="sxs-lookup"><span data-stu-id="b12bc-116">Description</span></span> |
| --- | ----------- |
| [**\<linkedConfiguration>**](linkedconfiguration-element.md) | <span data-ttu-id="b12bc-117">指定要包含的組態檔。</span><span class="sxs-lookup"><span data-stu-id="b12bc-117">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="b12bc-118">備註</span><span class="sxs-lookup"><span data-stu-id="b12bc-118">Remarks</span></span>

<span data-ttu-id="b12bc-119">[**\<linkedConfiguration>**](linkedconfiguration-element.md)元素藉由允許應用程式佈建檔在已知位置中包含元件設定檔，而不是複製元件設定，來簡化元件元件的管理。</span><span class="sxs-lookup"><span data-stu-id="b12bc-119">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="b12bc-120">**\<linkedConfiguration>** 具有 Windows 並存資訊清單的應用程式不支援元素。</span><span class="sxs-lookup"><span data-stu-id="b12bc-120">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="b12bc-121">範例</span><span class="sxs-lookup"><span data-stu-id="b12bc-121">Example</span></span>

<span data-ttu-id="b12bc-122">下列範例顯示如何將設定檔包含在本機硬碟上：</span><span class="sxs-lookup"><span data-stu-id="b12bc-122">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="b12bc-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b12bc-123">See also</span></span>

- [<span data-ttu-id="b12bc-124">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="b12bc-124">Configuration file schema for the .NET Framework</span></span>](index.md)

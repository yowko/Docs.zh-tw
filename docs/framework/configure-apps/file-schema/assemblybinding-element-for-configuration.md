---
title: <configuration> 的 <assemblyBinding> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: e0b83c4b3573ab6819654e72cac1bf3e4a0ba637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921266"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="3e2d8-102">\<configuration > 的\<assemblyBinding > 元素</span><span class="sxs-lookup"><span data-stu-id="3e2d8-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="3e2d8-103">指定位於組態層級的組件繫結原則。</span><span class="sxs-lookup"><span data-stu-id="3e2d8-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="3e2d8-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3e2d8-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="3e2d8-105">&nbsp;&nbsp; **\<assemblyBinding>**</span><span class="sxs-lookup"><span data-stu-id="3e2d8-105">&nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3e2d8-106">語法</span><span class="sxs-lookup"><span data-stu-id="3e2d8-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="3e2d8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3e2d8-107">Attribute</span></span>

|           | <span data-ttu-id="3e2d8-108">描述</span><span class="sxs-lookup"><span data-stu-id="3e2d8-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="3e2d8-109">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="3e2d8-109">**xmlns**</span></span> | <span data-ttu-id="3e2d8-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="3e2d8-110">Required attribute.</span></span><br><br><span data-ttu-id="3e2d8-111">指定組件繫結所需的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="3e2d8-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="3e2d8-112">使用字串 "urn:schemas-microsoft-com:asm.v1" 做為值。</span><span class="sxs-lookup"><span data-stu-id="3e2d8-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="3e2d8-113">父項目</span><span class="sxs-lookup"><span data-stu-id="3e2d8-113">Parent element</span></span>

|     | <span data-ttu-id="3e2d8-114">描述</span><span class="sxs-lookup"><span data-stu-id="3e2d8-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3e2d8-115"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="3e2d8-115">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="3e2d8-116">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="3e2d8-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="3e2d8-117">子項目</span><span class="sxs-lookup"><span data-stu-id="3e2d8-117">Child element</span></span>

|     | <span data-ttu-id="3e2d8-118">描述</span><span class="sxs-lookup"><span data-stu-id="3e2d8-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3e2d8-119"> **\<linkedConfiguration>** </span><span class="sxs-lookup"><span data-stu-id="3e2d8-119">**\<linkedConfiguration>**</span></span>](linkedconfiguration-element.md) | <span data-ttu-id="3e2d8-120">指定要包含的組態檔。</span><span class="sxs-lookup"><span data-stu-id="3e2d8-120">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3e2d8-121">備註</span><span class="sxs-lookup"><span data-stu-id="3e2d8-121">Remarks</span></span>

<span data-ttu-id="3e2d8-122">LinkedConfiguration > 元素藉由允許應用程式佈建檔在已知位置中包含元件設定檔, 而不是複製元件, 來簡化元件元件的管理。 [ **\<** ](linkedconfiguration-element.md)設定。</span><span class="sxs-lookup"><span data-stu-id="3e2d8-122">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="3e2d8-123">**\<LinkedConfiguration >** 與 Windows 並排顯示的資訊清單的應用程式不支援項目。</span><span class="sxs-lookup"><span data-stu-id="3e2d8-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="3e2d8-124">範例</span><span class="sxs-lookup"><span data-stu-id="3e2d8-124">Example</span></span>

<span data-ttu-id="3e2d8-125">下列範例顯示如何將設定檔包含在本機硬碟上:</span><span class="sxs-lookup"><span data-stu-id="3e2d8-125">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="3e2d8-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e2d8-126">See also</span></span>

- [<span data-ttu-id="3e2d8-127">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="3e2d8-127">Configuration file schema for the .NET Framework</span></span>](index.md)

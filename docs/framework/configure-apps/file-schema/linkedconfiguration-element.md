---
title: '&lt;linkedConfiguration&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 71769efa1233fc8a693219dc02ae56ea39c164e7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743793"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="46748-102">\<linkedConfiguration > 項目</span><span class="sxs-lookup"><span data-stu-id="46748-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="46748-103">指定要包含的組態檔。</span><span class="sxs-lookup"><span data-stu-id="46748-103">Specifies a configuration file to include.</span></span>

<span data-ttu-id="46748-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="46748-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="46748-105">&nbsp;&nbsp;[**\<assemblyBinding >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="46748-105">&nbsp;&nbsp;[**\<assemblyBinding>**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span></span>  
<span data-ttu-id="46748-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration >**</span><span class="sxs-lookup"><span data-stu-id="46748-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="46748-107">語法</span><span class="sxs-lookup"><span data-stu-id="46748-107">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="46748-108">屬性</span><span class="sxs-lookup"><span data-stu-id="46748-108">Attribute</span></span>

|           | <span data-ttu-id="46748-109">描述</span><span class="sxs-lookup"><span data-stu-id="46748-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="46748-110">**href**</span><span class="sxs-lookup"><span data-stu-id="46748-110">**href**</span></span>  | <span data-ttu-id="46748-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="46748-111">Required attribute.</span></span><br><br><span data-ttu-id="46748-112">包含組態檔的 URL。</span><span class="sxs-lookup"><span data-stu-id="46748-112">The URL of the configuration file to include.</span></span> <span data-ttu-id="46748-113">唯一支援的格式**href**屬性是`file://`。</span><span class="sxs-lookup"><span data-stu-id="46748-113">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="46748-114">支援本機檔案及 UNC 檔案。</span><span class="sxs-lookup"><span data-stu-id="46748-114">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="46748-115">父項目</span><span class="sxs-lookup"><span data-stu-id="46748-115">Parent element</span></span>

|     | <span data-ttu-id="46748-116">描述</span><span class="sxs-lookup"><span data-stu-id="46748-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="46748-117">**\<assemblyBinding >** 項目</span><span class="sxs-lookup"><span data-stu-id="46748-117">**\<assemblyBinding>** Element</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="46748-118">指定位於組態層級的組件繫結原則。</span><span class="sxs-lookup"><span data-stu-id="46748-118">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="46748-119">子元素</span><span class="sxs-lookup"><span data-stu-id="46748-119">Child elements</span></span>

<span data-ttu-id="46748-120">無</span><span class="sxs-lookup"><span data-stu-id="46748-120">None</span></span>

## <a name="remarks"></a><span data-ttu-id="46748-121">備註</span><span class="sxs-lookup"><span data-stu-id="46748-121">Remarks</span></span>

<span data-ttu-id="46748-122">**\<LinkedConfiguration >** 項目可簡化元件組件的服務。</span><span class="sxs-lookup"><span data-stu-id="46748-122">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="46748-123">如果一或多個應用程式使用具有組態檔中的已知位置的組件，可以使用使用組件的應用程式的組態檔 **\<linkedConfiguration >** 包含組件組態檔中，而不是直接包含組態資訊的項目。</span><span class="sxs-lookup"><span data-stu-id="46748-123">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="46748-124">當已服務元件組件時，更新通用的組態檔提供使用組件的所有應用程式更新的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="46748-124">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="46748-125">**\<LinkedConfiguration >** 項目不支援有 Windows-並存資訊清單的應用程式。</span><span class="sxs-lookup"><span data-stu-id="46748-125">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="46748-126">下列規則可管理使用連結的組態檔：</span><span class="sxs-lookup"><span data-stu-id="46748-126">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="46748-127">包含的組態檔中的設定只會影響載入器繫結原則，且僅供載入器。</span><span class="sxs-lookup"><span data-stu-id="46748-127">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="46748-128">包含的組態檔可以有繫結原則，以外的設定，但是這些設定不會有任何效果。</span><span class="sxs-lookup"><span data-stu-id="46748-128">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="46748-129">唯一支援的格式`href`屬性是`file://`。</span><span class="sxs-lookup"><span data-stu-id="46748-129">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="46748-130">支援本機檔案及 UNC 檔案。</span><span class="sxs-lookup"><span data-stu-id="46748-130">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="46748-131">連結的組態，每個組態檔的數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="46748-131">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="46748-132">所有連結的組態檔會合併成一個檔案，類似的行為`#include`C/c + + 中的指示詞。</span><span class="sxs-lookup"><span data-stu-id="46748-132">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="46748-133">**\<LinkedConfiguration >** 項目只允許在應用程式組態檔，則會忽略在*Machine.config*。</span><span class="sxs-lookup"><span data-stu-id="46748-133">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="46748-134">已偵測到循環參考，並終止。</span><span class="sxs-lookup"><span data-stu-id="46748-134">Circular references are detected and terminated.</span></span> <span data-ttu-id="46748-135">也就是說，如果 **\<linkedConfiguration >** 的一系列的組態檔項目形成迴圈，會偵測到迴圈，並將其停止。</span><span class="sxs-lookup"><span data-stu-id="46748-135">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="46748-136">範例</span><span class="sxs-lookup"><span data-stu-id="46748-136">Example</span></span>

<span data-ttu-id="46748-137">下列範例會示範如何包含從本機硬碟的組態檔：</span><span class="sxs-lookup"><span data-stu-id="46748-137">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="46748-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46748-138">See also</span></span>

<span data-ttu-id="46748-139">[**\<assemblyBinding >** 項目](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="46748-139">[**\<assemblyBinding>** Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span></span>  
[<span data-ttu-id="46748-140">適用於.NET Framework 組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="46748-140">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)

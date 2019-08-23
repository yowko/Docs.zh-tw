---
title: <linkedConfiguration> 項目
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
ms.openlocfilehash: a0b56ac66302f11c59c149197a84bb96691282a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921006"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="6b5e2-102">\<linkedConfiguration > 元素</span><span class="sxs-lookup"><span data-stu-id="6b5e2-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="6b5e2-103">指定要包含的組態檔。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-103">Specifies a configuration file to include.</span></span>

<span data-ttu-id="6b5e2-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6b5e2-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="6b5e2-105">&nbsp;&nbsp;[ **\<assemblyBinding>** ](assemblybinding-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="6b5e2-105">&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) </span></span>  
<span data-ttu-id="6b5e2-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration>**</span><span class="sxs-lookup"><span data-stu-id="6b5e2-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6b5e2-107">語法</span><span class="sxs-lookup"><span data-stu-id="6b5e2-107">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="6b5e2-108">屬性</span><span class="sxs-lookup"><span data-stu-id="6b5e2-108">Attribute</span></span>

|           | <span data-ttu-id="6b5e2-109">描述</span><span class="sxs-lookup"><span data-stu-id="6b5e2-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="6b5e2-110">**href**</span><span class="sxs-lookup"><span data-stu-id="6b5e2-110">**href**</span></span>  | <span data-ttu-id="6b5e2-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-111">Required attribute.</span></span><br><br><span data-ttu-id="6b5e2-112">要包含的設定檔的 URL。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-112">The URL of the configuration file to include.</span></span> <span data-ttu-id="6b5e2-113">**Href**屬性唯一支援的格式為`file://`。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-113">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="6b5e2-114">支援本機檔案和 UNC 檔案。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-114">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="6b5e2-115">父項目</span><span class="sxs-lookup"><span data-stu-id="6b5e2-115">Parent element</span></span>

|     | <span data-ttu-id="6b5e2-116">描述</span><span class="sxs-lookup"><span data-stu-id="6b5e2-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6b5e2-117"> **assemblyBinding>\<** 元素</span><span class="sxs-lookup"><span data-stu-id="6b5e2-117">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="6b5e2-118">指定位於組態層級的組件繫結原則。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-118">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="6b5e2-119">子元素</span><span class="sxs-lookup"><span data-stu-id="6b5e2-119">Child elements</span></span>

<span data-ttu-id="6b5e2-120">無</span><span class="sxs-lookup"><span data-stu-id="6b5e2-120">None</span></span>

## <a name="remarks"></a><span data-ttu-id="6b5e2-121">備註</span><span class="sxs-lookup"><span data-stu-id="6b5e2-121">Remarks</span></span>

<span data-ttu-id="6b5e2-122">LinkedConfiguration > 元素會簡化元件元件的服務。 **\<**</span><span class="sxs-lookup"><span data-stu-id="6b5e2-122">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="6b5e2-123">如果一或多個應用程式使用的元件具有位於已知位置的設定檔, 則使用該元件之應用程式的設定檔案可以使用 **\<linkedConfiguration >** 元素來包含元件設定檔, 而不是直接包含設定資訊。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-123">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="6b5e2-124">服務元件元件時, 更新通用設定檔案會將更新的設定資訊提供給所有使用該元件的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-124">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="6b5e2-125">**
          \<LinkedConfiguration >** 與 Windows 並排顯示的資訊清單的應用程式不支援項目。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-125">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="6b5e2-126">下列規則會管理連結的設定檔使用:</span><span class="sxs-lookup"><span data-stu-id="6b5e2-126">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="6b5e2-127">包含的設定檔案中的設定只會影響載入器系結原則, 而且僅供載入器使用。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-127">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="6b5e2-128">包含的設定檔案可以具有系結原則以外的設定, 但這些設定不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-128">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="6b5e2-129">`href`屬性唯一支援的格式為`file://`。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-129">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="6b5e2-130">支援本機檔案和 UNC 檔案。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-130">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="6b5e2-131">每個設定檔的連結設定數目沒有條件約束。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-131">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="6b5e2-132">所有連結的設定檔都會合並成一個檔案, 類似于 C/ `#include` C++中指示詞的行為。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-132">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="6b5e2-133">只有在應用程式佈建檔中,  **\<才允許 linkedConfiguration >** 元素; machine.config 中會忽略它。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-133">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="6b5e2-134">偵測到迴圈參考並結束。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-134">Circular references are detected and terminated.</span></span> <span data-ttu-id="6b5e2-135">也就是說, 如果 **\<linkedConfiguration >** 一系列設定檔中的元素形成迴圈, 就會偵測到迴圈並停止。</span><span class="sxs-lookup"><span data-stu-id="6b5e2-135">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="6b5e2-136">範例</span><span class="sxs-lookup"><span data-stu-id="6b5e2-136">Example</span></span>

<span data-ttu-id="6b5e2-137">下列範例顯示如何包含本機硬碟的設定檔:</span><span class="sxs-lookup"><span data-stu-id="6b5e2-137">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="6b5e2-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b5e2-138">See also</span></span>

- [<span data-ttu-id="6b5e2-139"> **assemblyBinding>\<** 元素</span><span class="sxs-lookup"><span data-stu-id="6b5e2-139">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="6b5e2-140">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="6b5e2-140">Configuration file schema for the .NET Framework</span></span>](index.md)

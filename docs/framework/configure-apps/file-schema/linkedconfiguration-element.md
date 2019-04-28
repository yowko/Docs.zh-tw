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
ms.openlocfilehash: 909ee7cbb7cd31cf213f305b23237cb69e295882
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674645"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="37d1f-102">\<linkedConfiguration > 項目</span><span class="sxs-lookup"><span data-stu-id="37d1f-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="37d1f-103">指定要包含的組態檔。</span><span class="sxs-lookup"><span data-stu-id="37d1f-103">Specifies a configuration file to include.</span></span>

<span data-ttu-id="37d1f-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="37d1f-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="37d1f-105">&nbsp;&nbsp;[**\<assemblyBinding>**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="37d1f-105">&nbsp;&nbsp;[**\<assemblyBinding>**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span></span>  
<span data-ttu-id="37d1f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span><span class="sxs-lookup"><span data-stu-id="37d1f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="37d1f-107">語法</span><span class="sxs-lookup"><span data-stu-id="37d1f-107">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="37d1f-108">屬性</span><span class="sxs-lookup"><span data-stu-id="37d1f-108">Attribute</span></span>

|           | <span data-ttu-id="37d1f-109">描述</span><span class="sxs-lookup"><span data-stu-id="37d1f-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="37d1f-110">**href**</span><span class="sxs-lookup"><span data-stu-id="37d1f-110">**href**</span></span>  | <span data-ttu-id="37d1f-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="37d1f-111">Required attribute.</span></span><br><br><span data-ttu-id="37d1f-112">包含組態檔的 URL。</span><span class="sxs-lookup"><span data-stu-id="37d1f-112">The URL of the configuration file to include.</span></span> <span data-ttu-id="37d1f-113">唯一支援的格式**href**屬性是`file://`。</span><span class="sxs-lookup"><span data-stu-id="37d1f-113">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="37d1f-114">支援本機檔案和 UNC 檔案。</span><span class="sxs-lookup"><span data-stu-id="37d1f-114">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="37d1f-115">父項目</span><span class="sxs-lookup"><span data-stu-id="37d1f-115">Parent element</span></span>

|     | <span data-ttu-id="37d1f-116">描述</span><span class="sxs-lookup"><span data-stu-id="37d1f-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="37d1f-117">**\<Assemblybinding> >** 項目</span><span class="sxs-lookup"><span data-stu-id="37d1f-117">**\<assemblyBinding>** Element</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="37d1f-118">指定位於組態層級的組件繫結原則。</span><span class="sxs-lookup"><span data-stu-id="37d1f-118">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="37d1f-119">子元素</span><span class="sxs-lookup"><span data-stu-id="37d1f-119">Child elements</span></span>

<span data-ttu-id="37d1f-120">None</span><span class="sxs-lookup"><span data-stu-id="37d1f-120">None</span></span>

## <a name="remarks"></a><span data-ttu-id="37d1f-121">備註</span><span class="sxs-lookup"><span data-stu-id="37d1f-121">Remarks</span></span>

<span data-ttu-id="37d1f-122"> *\*\<LinkedConfiguration >** 項目可簡化元件組件的服務。</span><span class="sxs-lookup"><span data-stu-id="37d1f-122">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="37d1f-123">如果一或多個應用程式會使用具有組態檔位於已知位置中的組件，可以使用使用組件的應用程式的組態檔 **\<linkedConfiguration >** 包含組件的組態檔，而不是直接包括組態資訊的項目。</span><span class="sxs-lookup"><span data-stu-id="37d1f-123">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="37d1f-124">當元件組件受到服務時，更新常見的組態檔提供使用組件的所有應用程式的更新的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="37d1f-124">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="37d1f-125">**\<LinkedConfiguration >** 與 Windows 並排顯示的資訊清單的應用程式不支援項目。</span><span class="sxs-lookup"><span data-stu-id="37d1f-125">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="37d1f-126">下列規則管理連結的組態檔的使用：</span><span class="sxs-lookup"><span data-stu-id="37d1f-126">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="37d1f-127">包含的組態檔中設定只會影響載入器繫結原則，且僅供載入器。</span><span class="sxs-lookup"><span data-stu-id="37d1f-127">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="37d1f-128">包含的組態檔可能會有非繫結原則，設定，但這些設定不具有任何作用。</span><span class="sxs-lookup"><span data-stu-id="37d1f-128">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="37d1f-129">唯一支援的格式`href`屬性是`file://`。</span><span class="sxs-lookup"><span data-stu-id="37d1f-129">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="37d1f-130">支援本機檔案和 UNC 檔案。</span><span class="sxs-lookup"><span data-stu-id="37d1f-130">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="37d1f-131">連結的組態，每個組態檔的數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="37d1f-131">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="37d1f-132">所有連結的組態檔會合併以形成一個檔案，類似的行為`#include`指示詞 C /C++。</span><span class="sxs-lookup"><span data-stu-id="37d1f-132">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="37d1f-133"> *\*\<LinkedConfiguration >** 項目只允許在應用程式組態檔，它會忽略\*Machine.config\*。</span><span class="sxs-lookup"><span data-stu-id="37d1f-133">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="37d1f-134">已偵測到循環參考，並終止。</span><span class="sxs-lookup"><span data-stu-id="37d1f-134">Circular references are detected and terminated.</span></span> <span data-ttu-id="37d1f-135">也就是說，如果 **\<linkedConfiguration >** 的一系列的組態檔項目形成迴圈，是偵測到迴圈，並將其停止。</span><span class="sxs-lookup"><span data-stu-id="37d1f-135">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="37d1f-136">範例</span><span class="sxs-lookup"><span data-stu-id="37d1f-136">Example</span></span>

<span data-ttu-id="37d1f-137">下列範例示範如何包含從本機硬碟的組態檔：</span><span class="sxs-lookup"><span data-stu-id="37d1f-137">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="37d1f-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37d1f-138">See also</span></span>

- [<span data-ttu-id="37d1f-139">**\<Assemblybinding> >** 項目</span><span class="sxs-lookup"><span data-stu-id="37d1f-139">**\<assemblyBinding>** Element</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="37d1f-140">適用於.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="37d1f-140">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)

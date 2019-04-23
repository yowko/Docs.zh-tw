---
title: < Crst_DisableSpinWait > 項目
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cde26250db0b3d11c51a18b7ebd378953ae0958
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981252"
---
# <a name="crstdisablespinwait-element"></a><span data-ttu-id="e2df5-102">\<Crst_DisableSpinWait > 項目</span><span class="sxs-lookup"><span data-stu-id="e2df5-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="e2df5-103">指定是否要停用微調-等候時爭用重要區段。</span><span class="sxs-lookup"><span data-stu-id="e2df5-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span> \ 
  
 <span data-ttu-id="e2df5-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e2df5-104">\<configuration></span></span>  
<span data-ttu-id="e2df5-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="e2df5-105">\<runtime></span></span>  
<span data-ttu-id="e2df5-106">\<Crst_DisableSpinWait></span><span class="sxs-lookup"><span data-stu-id="e2df5-106">\<Crst_DisableSpinWait></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2df5-107">語法</span><span class="sxs-lookup"><span data-stu-id="e2df5-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2df5-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e2df5-108">Attributes and Elements</span></span>

<span data-ttu-id="e2df5-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e2df5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2df5-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e2df5-110">Attributes</span></span>  
  
|<span data-ttu-id="e2df5-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e2df5-111">Attribute</span></span>|<span data-ttu-id="e2df5-112">描述</span><span class="sxs-lookup"><span data-stu-id="e2df5-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2df5-113">**enabled**</span><span class="sxs-lookup"><span data-stu-id="e2df5-113">**enabled**</span></span>|<span data-ttu-id="e2df5-114">指定是否要在其爭用時，啟用關鍵區段旋轉等待。</span><span class="sxs-lookup"><span data-stu-id="e2df5-114">Specifies whether spin-waiting for critical sections is enabled when they are contended.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e2df5-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="e2df5-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="e2df5-116">值</span><span class="sxs-lookup"><span data-stu-id="e2df5-116">Value</span></span>|<span data-ttu-id="e2df5-117">描述</span><span class="sxs-lookup"><span data-stu-id="e2df5-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e2df5-118">1</span><span class="sxs-lookup"><span data-stu-id="e2df5-118">1</span></span>|<span data-ttu-id="e2df5-119">微調等待已啟用。</span><span class="sxs-lookup"><span data-stu-id="e2df5-119">Spin-waiting is enabled.</span></span>|  
|<span data-ttu-id="e2df5-120">0</span><span class="sxs-lookup"><span data-stu-id="e2df5-120">0</span></span>|<span data-ttu-id="e2df5-121">微調等待已停用。</span><span class="sxs-lookup"><span data-stu-id="e2df5-121">Spin-waiting is disabled.</span></span> <span data-ttu-id="e2df5-122">這是預設值</span><span class="sxs-lookup"><span data-stu-id="e2df5-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2df5-123">子元素</span><span class="sxs-lookup"><span data-stu-id="e2df5-123">Child Elements</span></span>  
 <span data-ttu-id="e2df5-124">無。</span><span class="sxs-lookup"><span data-stu-id="e2df5-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e2df5-125">父項目</span><span class="sxs-lookup"><span data-stu-id="e2df5-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e2df5-126">項目</span><span class="sxs-lookup"><span data-stu-id="e2df5-126">Element</span></span>|<span data-ttu-id="e2df5-127">描述</span><span class="sxs-lookup"><span data-stu-id="e2df5-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e2df5-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="e2df5-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e2df5-129">包含執行階段的各種組態設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e2df5-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e2df5-130">範例</span><span class="sxs-lookup"><span data-stu-id="e2df5-130">Example</span></span>  

<span data-ttu-id="e2df5-131">下列範例會停用微調等候爭用時的關鍵區段中。</span><span class="sxs-lookup"><span data-stu-id="e2df5-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2df5-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2df5-132">See also</span></span>

- [<span data-ttu-id="e2df5-133">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e2df5-133">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="e2df5-134">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="e2df5-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)

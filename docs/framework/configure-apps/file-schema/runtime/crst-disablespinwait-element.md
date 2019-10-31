---
title: < Crst_DisableSpinWait > 元素
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: 0683081183081e249b2a9c89e1a6a15f638fb339
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117643"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="04133-102">\<Crst_DisableSpinWait > 元素</span><span class="sxs-lookup"><span data-stu-id="04133-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="04133-103">指定是否要在爭用時停用微調等候重要區段。</span><span class="sxs-lookup"><span data-stu-id="04133-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
<span data-ttu-id="04133-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="04133-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="04133-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="04133-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="04133-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Crst_DisableSpinWait >**</span><span class="sxs-lookup"><span data-stu-id="04133-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04133-107">語法</span><span class="sxs-lookup"><span data-stu-id="04133-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04133-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="04133-108">Attributes and Elements</span></span>

<span data-ttu-id="04133-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="04133-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04133-110">屬性</span><span class="sxs-lookup"><span data-stu-id="04133-110">Attributes</span></span>  
  
|<span data-ttu-id="04133-111">屬性</span><span class="sxs-lookup"><span data-stu-id="04133-111">Attribute</span></span>|<span data-ttu-id="04133-112">描述</span><span class="sxs-lookup"><span data-stu-id="04133-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04133-113">**後**</span><span class="sxs-lookup"><span data-stu-id="04133-113">**enabled**</span></span>|<span data-ttu-id="04133-114">指定在停用時，是否要微調等候重要區段。</span><span class="sxs-lookup"><span data-stu-id="04133-114">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="04133-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="04133-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="04133-116">值</span><span class="sxs-lookup"><span data-stu-id="04133-116">Value</span></span>|<span data-ttu-id="04133-117">描述</span><span class="sxs-lookup"><span data-stu-id="04133-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04133-118">1</span><span class="sxs-lookup"><span data-stu-id="04133-118">1</span></span>|<span data-ttu-id="04133-119">當無法取得重要區段時，停用微調等候。</span><span class="sxs-lookup"><span data-stu-id="04133-119">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="04133-120">0</span><span class="sxs-lookup"><span data-stu-id="04133-120">0</span></span>|<span data-ttu-id="04133-121">當無法取得重要區段時，請勿停用微調等候。</span><span class="sxs-lookup"><span data-stu-id="04133-121">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="04133-122">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="04133-122">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04133-123">子項目</span><span class="sxs-lookup"><span data-stu-id="04133-123">Child Elements</span></span>  
 <span data-ttu-id="04133-124">無。</span><span class="sxs-lookup"><span data-stu-id="04133-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04133-125">父項目</span><span class="sxs-lookup"><span data-stu-id="04133-125">Parent Elements</span></span>  
  
|<span data-ttu-id="04133-126">項目</span><span class="sxs-lookup"><span data-stu-id="04133-126">Element</span></span>|<span data-ttu-id="04133-127">描述</span><span class="sxs-lookup"><span data-stu-id="04133-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="04133-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="04133-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="04133-129">包含各種執行時間設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="04133-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="04133-130">範例</span><span class="sxs-lookup"><span data-stu-id="04133-130">Example</span></span>  

<span data-ttu-id="04133-131">下列範例會在爭用時停用關鍵區段中的微調等候。</span><span class="sxs-lookup"><span data-stu-id="04133-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="04133-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="04133-132">See also</span></span>

- [<span data-ttu-id="04133-133">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="04133-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="04133-134">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="04133-134">Configuration File Schema</span></span>](../index.md)

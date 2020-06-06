---
title: <Crst_DisableSpinWait> 元素
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: 0683081183081e249b2a9c89e1a6a15f638fb339
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117643"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="489dd-102">\<Crst_DisableSpinWait> 項目</span><span class="sxs-lookup"><span data-stu-id="489dd-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="489dd-103">指定是否要在爭用時停用微調等候重要區段。</span><span class="sxs-lookup"><span data-stu-id="489dd-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**  
  
## <a name="syntax"></a><span data-ttu-id="489dd-104">語法</span><span class="sxs-lookup"><span data-stu-id="489dd-104">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="489dd-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="489dd-105">Attributes and Elements</span></span>

<span data-ttu-id="489dd-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="489dd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="489dd-107">屬性</span><span class="sxs-lookup"><span data-stu-id="489dd-107">Attributes</span></span>  
  
|<span data-ttu-id="489dd-108">屬性</span><span class="sxs-lookup"><span data-stu-id="489dd-108">Attribute</span></span>|<span data-ttu-id="489dd-109">描述</span><span class="sxs-lookup"><span data-stu-id="489dd-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="489dd-110">**後**</span><span class="sxs-lookup"><span data-stu-id="489dd-110">**enabled**</span></span>|<span data-ttu-id="489dd-111">指定在停用時，是否要微調等候重要區段。</span><span class="sxs-lookup"><span data-stu-id="489dd-111">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="489dd-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="489dd-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="489dd-113">值</span><span class="sxs-lookup"><span data-stu-id="489dd-113">Value</span></span>|<span data-ttu-id="489dd-114">描述</span><span class="sxs-lookup"><span data-stu-id="489dd-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="489dd-115">1</span><span class="sxs-lookup"><span data-stu-id="489dd-115">1</span></span>|<span data-ttu-id="489dd-116">當無法取得重要區段時，停用微調等候。</span><span class="sxs-lookup"><span data-stu-id="489dd-116">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="489dd-117">0</span><span class="sxs-lookup"><span data-stu-id="489dd-117">0</span></span>|<span data-ttu-id="489dd-118">當無法取得重要區段時，請勿停用微調等候。</span><span class="sxs-lookup"><span data-stu-id="489dd-118">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="489dd-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="489dd-119">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="489dd-120">子元素</span><span class="sxs-lookup"><span data-stu-id="489dd-120">Child Elements</span></span>  
 <span data-ttu-id="489dd-121">無。</span><span class="sxs-lookup"><span data-stu-id="489dd-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="489dd-122">父項目</span><span class="sxs-lookup"><span data-stu-id="489dd-122">Parent Elements</span></span>  
  
|<span data-ttu-id="489dd-123">元素</span><span class="sxs-lookup"><span data-stu-id="489dd-123">Element</span></span>|<span data-ttu-id="489dd-124">描述</span><span class="sxs-lookup"><span data-stu-id="489dd-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="489dd-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="489dd-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="489dd-126">包含各種執行時間設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="489dd-126">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="489dd-127">範例</span><span class="sxs-lookup"><span data-stu-id="489dd-127">Example</span></span>  

<span data-ttu-id="489dd-128">下列範例會在爭用時停用關鍵區段中的微調等候。</span><span class="sxs-lookup"><span data-stu-id="489dd-128">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="489dd-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="489dd-129">See also</span></span>

- [<span data-ttu-id="489dd-130">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="489dd-130">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="489dd-131">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="489dd-131">Configuration File Schema</span></span>](../index.md)

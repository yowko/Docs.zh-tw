---
title: <Crst_DisableSpinWait> 元素
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: 45052d99bb297ac39d058fa405fe57a7c991f738
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151346"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="48e80-102">\<Crst_DisableSpinWait> 項目</span><span class="sxs-lookup"><span data-stu-id="48e80-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="48e80-103">指定是否要在發生爭用時，停用微調等候的重要區段。</span><span class="sxs-lookup"><span data-stu-id="48e80-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**  
  
## <a name="syntax"></a><span data-ttu-id="48e80-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="48e80-104">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48e80-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="48e80-105">Attributes and Elements</span></span>

<span data-ttu-id="48e80-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="48e80-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48e80-107">屬性</span><span class="sxs-lookup"><span data-stu-id="48e80-107">Attributes</span></span>  
  
|<span data-ttu-id="48e80-108">屬性</span><span class="sxs-lookup"><span data-stu-id="48e80-108">Attribute</span></span>|<span data-ttu-id="48e80-109">描述</span><span class="sxs-lookup"><span data-stu-id="48e80-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="48e80-110">**啟用**</span><span class="sxs-lookup"><span data-stu-id="48e80-110">**enabled**</span></span>|<span data-ttu-id="48e80-111">指定是否要在爭用的重要區段停用時，對其進行微調。</span><span class="sxs-lookup"><span data-stu-id="48e80-111">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="48e80-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="48e80-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="48e80-113">值</span><span class="sxs-lookup"><span data-stu-id="48e80-113">Value</span></span>|<span data-ttu-id="48e80-114">描述</span><span class="sxs-lookup"><span data-stu-id="48e80-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="48e80-115">1</span><span class="sxs-lookup"><span data-stu-id="48e80-115">1</span></span>|<span data-ttu-id="48e80-116">當無法取得重要區段時，請停用旋轉等候。</span><span class="sxs-lookup"><span data-stu-id="48e80-116">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="48e80-117">0</span><span class="sxs-lookup"><span data-stu-id="48e80-117">0</span></span>|<span data-ttu-id="48e80-118">當無法取得重要區段時，請勿停用旋轉等候。</span><span class="sxs-lookup"><span data-stu-id="48e80-118">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="48e80-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="48e80-119">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48e80-120">子元素</span><span class="sxs-lookup"><span data-stu-id="48e80-120">Child Elements</span></span>  

 <span data-ttu-id="48e80-121">無。</span><span class="sxs-lookup"><span data-stu-id="48e80-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="48e80-122">父項目</span><span class="sxs-lookup"><span data-stu-id="48e80-122">Parent Elements</span></span>  
  
|<span data-ttu-id="48e80-123">項目</span><span class="sxs-lookup"><span data-stu-id="48e80-123">Element</span></span>|<span data-ttu-id="48e80-124">描述</span><span class="sxs-lookup"><span data-stu-id="48e80-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="48e80-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="48e80-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="48e80-126">包含各種執行時間設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="48e80-126">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="48e80-127">範例</span><span class="sxs-lookup"><span data-stu-id="48e80-127">Example</span></span>  

<span data-ttu-id="48e80-128">下列範例會在發生爭用時，停用重要區段中的旋轉等候。</span><span class="sxs-lookup"><span data-stu-id="48e80-128">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48e80-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48e80-129">See also</span></span>

- [<span data-ttu-id="48e80-130">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="48e80-130">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="48e80-131">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="48e80-131">Configuration File Schema</span></span>](../index.md)

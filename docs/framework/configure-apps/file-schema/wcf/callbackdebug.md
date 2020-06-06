---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 92a8fa83b5cf5f429278ac8edc8439b627839aad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400561"
---
# \<callbackDebug>
<span data-ttu-id="ff1c4-101">指定 Windows Communication Foundation （WCF）回呼物件的服務偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="ff1c4-101">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackDebug>**  
  
## <a name="syntax"></a><span data-ttu-id="ff1c4-102">語法</span><span class="sxs-lookup"><span data-stu-id="ff1c4-102">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="ff1c4-103">類型</span><span class="sxs-lookup"><span data-stu-id="ff1c4-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff1c4-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ff1c4-104">Attributes and Elements</span></span>  
 <span data-ttu-id="ff1c4-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ff1c4-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff1c4-106">屬性</span><span class="sxs-lookup"><span data-stu-id="ff1c4-106">Attributes</span></span>  
  
|<span data-ttu-id="ff1c4-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ff1c4-107">Attribute</span></span>|<span data-ttu-id="ff1c4-108">描述</span><span class="sxs-lookup"><span data-stu-id="ff1c4-108">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="ff1c4-109">這個值會指定用戶端回呼物件是否將 SOAP 錯誤中的 Managed 例外狀況資訊傳回給服務。</span><span class="sxs-lookup"><span data-stu-id="ff1c4-109">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="ff1c4-110">如果您以程式設計方式將這個屬性設定為 `true`，您可以讓用戶端回呼物件中的 Managed 例外狀況資訊的流動回到服務，以達偵錯的目的。</span><span class="sxs-lookup"><span data-stu-id="ff1c4-110">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="ff1c4-111">**注意：** 將 managed 例外狀況資訊傳回給用戶端可能會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="ff1c4-111">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="ff1c4-112">這是因為例外狀況細節會公開內部服務實作 (Implementation) 的相關資訊，可能會被未經授權的用戶端加以利用。</span><span class="sxs-lookup"><span data-stu-id="ff1c4-112">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff1c4-113">子元素</span><span class="sxs-lookup"><span data-stu-id="ff1c4-113">Child Elements</span></span>  
 <span data-ttu-id="ff1c4-114">無。</span><span class="sxs-lookup"><span data-stu-id="ff1c4-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff1c4-115">父項目</span><span class="sxs-lookup"><span data-stu-id="ff1c4-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ff1c4-116">元素</span><span class="sxs-lookup"><span data-stu-id="ff1c4-116">Element</span></span>|<span data-ttu-id="ff1c4-117">描述</span><span class="sxs-lookup"><span data-stu-id="ff1c4-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ff1c4-118">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="ff1c4-118">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff1c4-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff1c4-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>

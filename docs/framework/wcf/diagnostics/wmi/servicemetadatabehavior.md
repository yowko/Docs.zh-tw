---
title: ServiceMetadataBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c05f6be9fc0507b7e2f1de4374e3b9bbe3e2a10e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="fed2b-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="fed2b-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="fed2b-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="fed2b-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fed2b-104">語法</span><span class="sxs-lookup"><span data-stu-id="fed2b-104">Syntax</span></span>  
  
```  
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fed2b-105">方法</span><span class="sxs-lookup"><span data-stu-id="fed2b-105">Methods</span></span>  
 <span data-ttu-id="fed2b-106">ServiceMetadataBehavior 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="fed2b-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fed2b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="fed2b-107">Properties</span></span>  
 <span data-ttu-id="fed2b-108">ServiceMetadataBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="fed2b-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="fed2b-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="fed2b-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="fed2b-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="fed2b-110">Data type: string</span></span>  
  
 <span data-ttu-id="fed2b-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fed2b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fed2b-112">設定服務重新導向中繼資料要求的位置。</span><span class="sxs-lookup"><span data-stu-id="fed2b-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="fed2b-113">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="fed2b-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="fed2b-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="fed2b-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="fed2b-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fed2b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fed2b-116">控制服務是否會在由 `HttpGetUrl` 屬性控制的位址發行其 WSDL。</span><span class="sxs-lookup"><span data-stu-id="fed2b-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="fed2b-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="fed2b-117">HttpGetUrl</span></span>  
 <span data-ttu-id="fed2b-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="fed2b-118">Data type: string</span></span>  
  
 <span data-ttu-id="fed2b-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fed2b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fed2b-120">設定服務 WSDL 的發行位置，以供使用 HTTP 擷取。</span><span class="sxs-lookup"><span data-stu-id="fed2b-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="fed2b-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="fed2b-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="fed2b-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="fed2b-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="fed2b-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fed2b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fed2b-124">控制服務是否會透過 HTTPS，在由 `HttpsGetUrl` 屬性控制的位址發行其 WSDL。</span><span class="sxs-lookup"><span data-stu-id="fed2b-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="fed2b-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="fed2b-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="fed2b-126">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="fed2b-126">Data type: string</span></span>  
  
 <span data-ttu-id="fed2b-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fed2b-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fed2b-128">設定服務 WSDL 的發行位置，以供使用 HTTPS 擷取。</span><span class="sxs-lookup"><span data-stu-id="fed2b-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fed2b-129">需求</span><span class="sxs-lookup"><span data-stu-id="fed2b-129">Requirements</span></span>  
  
|<span data-ttu-id="fed2b-130">MOF</span><span class="sxs-lookup"><span data-stu-id="fed2b-130">MOF</span></span>|<span data-ttu-id="fed2b-131">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="fed2b-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fed2b-132">命名空間</span><span class="sxs-lookup"><span data-stu-id="fed2b-132">Namespace</span></span>|<span data-ttu-id="fed2b-133">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="fed2b-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fed2b-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="fed2b-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>

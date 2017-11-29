---
title: ServiceDebugBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d6b866c90e3e6c6e72dc75f230bcf7b4e03a6bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="d0aed-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="d0aed-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="d0aed-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="d0aed-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0aed-104">語法</span><span class="sxs-lookup"><span data-stu-id="d0aed-104">Syntax</span></span>  
  
```  
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d0aed-105">方法</span><span class="sxs-lookup"><span data-stu-id="d0aed-105">Methods</span></span>  
 <span data-ttu-id="d0aed-106">ServiceDebugBehavior 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="d0aed-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d0aed-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d0aed-107">Properties</span></span>  
 <span data-ttu-id="d0aed-108">ServiceDebugBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d0aed-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="d0aed-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="d0aed-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="d0aed-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="d0aed-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="d0aed-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="d0aed-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0aed-112">控制服務是否會在由 `HttpGetUrl` 屬性控制的位址發行其 WSDL。</span><span class="sxs-lookup"><span data-stu-id="d0aed-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="d0aed-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="d0aed-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="d0aed-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="d0aed-114">Data type: string</span></span>  
  
 <span data-ttu-id="d0aed-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="d0aed-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0aed-116">設定服務 WSDL 的發行位置，以供使用 HTTP 擷取。</span><span class="sxs-lookup"><span data-stu-id="d0aed-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="d0aed-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="d0aed-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="d0aed-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="d0aed-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="d0aed-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="d0aed-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0aed-120">控制服務是否會透過 HTTPS，在由 `HttpsGetUrl` 屬性控制的位址發行其 WSDL。</span><span class="sxs-lookup"><span data-stu-id="d0aed-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="d0aed-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="d0aed-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="d0aed-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="d0aed-122">Data type: string</span></span>  
  
 <span data-ttu-id="d0aed-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="d0aed-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0aed-124">設定服務 WSDL 的發行位置，以供使用 HTTPS 擷取。</span><span class="sxs-lookup"><span data-stu-id="d0aed-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="d0aed-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="d0aed-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="d0aed-126">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="d0aed-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="d0aed-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="d0aed-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0aed-128">指定是否要針對偵錯用途，在傳回給用戶端的 SOAP 錯誤詳細資料中包含 Managed 例外狀況資訊。</span><span class="sxs-lookup"><span data-stu-id="d0aed-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0aed-129">需求</span><span class="sxs-lookup"><span data-stu-id="d0aed-129">Requirements</span></span>  
  
|<span data-ttu-id="d0aed-130">MOF</span><span class="sxs-lookup"><span data-stu-id="d0aed-130">MOF</span></span>|<span data-ttu-id="d0aed-131">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="d0aed-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d0aed-132">命名空間</span><span class="sxs-lookup"><span data-stu-id="d0aed-132">Namespace</span></span>|<span data-ttu-id="d0aed-133">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="d0aed-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0aed-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0aed-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>

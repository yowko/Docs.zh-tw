---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 1d99af064205447c2f11f6f19258551c1e88d386
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976129"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="a1a90-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="a1a90-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="a1a90-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="a1a90-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1a90-104">語法</span><span class="sxs-lookup"><span data-stu-id="a1a90-104">Syntax</span></span>  
  
```csharp
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a1a90-105">方法</span><span class="sxs-lookup"><span data-stu-id="a1a90-105">Methods</span></span>  
 <span data-ttu-id="a1a90-106">ServiceMetadataBehavior 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="a1a90-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a1a90-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a1a90-107">Properties</span></span>  
 <span data-ttu-id="a1a90-108">ServiceMetadataBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="a1a90-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="a1a90-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="a1a90-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="a1a90-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="a1a90-110">Data type: string</span></span>  
  
 <span data-ttu-id="a1a90-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a1a90-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a90-112">設定服務重新導向中繼資料要求的位置。</span><span class="sxs-lookup"><span data-stu-id="a1a90-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="a1a90-113">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="a1a90-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="a1a90-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="a1a90-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="a1a90-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a1a90-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a90-116">控制服務是否會在由 `HttpGetUrl` 屬性控制的位址發行其 WSDL。</span><span class="sxs-lookup"><span data-stu-id="a1a90-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="a1a90-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="a1a90-117">HttpGetUrl</span></span>  
 <span data-ttu-id="a1a90-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="a1a90-118">Data type: string</span></span>  
  
 <span data-ttu-id="a1a90-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a1a90-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a90-120">設定服務 WSDL 的發行位置，以供使用 HTTP 擷取。</span><span class="sxs-lookup"><span data-stu-id="a1a90-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="a1a90-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="a1a90-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="a1a90-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="a1a90-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="a1a90-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a1a90-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a90-124">控制服務是否會透過 HTTPS，在由 `HttpsGetUrl` 屬性控制的位址發行其 WSDL。</span><span class="sxs-lookup"><span data-stu-id="a1a90-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="a1a90-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="a1a90-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="a1a90-126">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="a1a90-126">Data type: string</span></span>  
  
 <span data-ttu-id="a1a90-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a1a90-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a90-128">設定服務 WSDL 的發行位置，以供使用 HTTPS 擷取。</span><span class="sxs-lookup"><span data-stu-id="a1a90-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1a90-129">需求</span><span class="sxs-lookup"><span data-stu-id="a1a90-129">Requirements</span></span>  
  
|<span data-ttu-id="a1a90-130">MOF</span><span class="sxs-lookup"><span data-stu-id="a1a90-130">MOF</span></span>|<span data-ttu-id="a1a90-131">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="a1a90-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a1a90-132">命名空間</span><span class="sxs-lookup"><span data-stu-id="a1a90-132">Namespace</span></span>|<span data-ttu-id="a1a90-133">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="a1a90-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1a90-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1a90-134">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>

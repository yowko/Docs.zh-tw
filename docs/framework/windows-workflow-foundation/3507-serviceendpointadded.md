---
title: 3507 - ServiceEndpointAdded
ms.date: 03/30/2017
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
ms.openlocfilehash: 903071e7b1f89dc3489b8d3ac05427d699a33a7e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240754"
---
# <a name="3507---serviceendpointadded"></a><span data-ttu-id="a3ae1-102">3507 - ServiceEndpointAdded</span><span class="sxs-lookup"><span data-stu-id="a3ae1-102">3507 - ServiceEndpointAdded</span></span>

## <a name="properties"></a><span data-ttu-id="a3ae1-103">屬性</span><span class="sxs-lookup"><span data-stu-id="a3ae1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a3ae1-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="a3ae1-104">ID</span></span>|<span data-ttu-id="a3ae1-105">3507</span><span class="sxs-lookup"><span data-stu-id="a3ae1-105">3507</span></span>|  
|<span data-ttu-id="a3ae1-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a3ae1-106">Keywords</span></span>|<span data-ttu-id="a3ae1-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="a3ae1-107">WFServices</span></span>|  
|<span data-ttu-id="a3ae1-108">層級</span><span class="sxs-lookup"><span data-stu-id="a3ae1-108">Level</span></span>|<span data-ttu-id="a3ae1-109">資訊</span><span class="sxs-lookup"><span data-stu-id="a3ae1-109">Information</span></span>|  
|<span data-ttu-id="a3ae1-110">通路</span><span class="sxs-lookup"><span data-stu-id="a3ae1-110">Channel</span></span>|<span data-ttu-id="a3ae1-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a3ae1-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a3ae1-112">描述</span><span class="sxs-lookup"><span data-stu-id="a3ae1-112">Description</span></span>  

 <span data-ttu-id="a3ae1-113">表示已加入服務端點。</span><span class="sxs-lookup"><span data-stu-id="a3ae1-113">Indicates a service endpoint has been added.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a3ae1-114">訊息</span><span class="sxs-lookup"><span data-stu-id="a3ae1-114">Message</span></span>  

 <span data-ttu-id="a3ae1-115">已經針對位址 '%1'、繫結 '%2' 和合約 '%3' 加入服務端點。</span><span class="sxs-lookup"><span data-stu-id="a3ae1-115">A service endpoint has been added for address '%1', binding '%2', and contract '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a3ae1-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a3ae1-116">Details</span></span>  
  
|<span data-ttu-id="a3ae1-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="a3ae1-117">Data Item Name</span></span>|<span data-ttu-id="a3ae1-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="a3ae1-118">Data Item Type</span></span>|<span data-ttu-id="a3ae1-119">描述</span><span class="sxs-lookup"><span data-stu-id="a3ae1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a3ae1-120">位址</span><span class="sxs-lookup"><span data-stu-id="a3ae1-120">Address</span></span>|<span data-ttu-id="a3ae1-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3ae1-121">xs:string</span></span>|<span data-ttu-id="a3ae1-122">端點的位址。</span><span class="sxs-lookup"><span data-stu-id="a3ae1-122">The address of the endpoint.</span></span>|  
|<span data-ttu-id="a3ae1-123">繫結</span><span class="sxs-lookup"><span data-stu-id="a3ae1-123">Binding</span></span>|<span data-ttu-id="a3ae1-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3ae1-124">xs:string</span></span>|<span data-ttu-id="a3ae1-125">端點的繫結。</span><span class="sxs-lookup"><span data-stu-id="a3ae1-125">The binding of the endpoint.</span></span>|  
|<span data-ttu-id="a3ae1-126">合約</span><span class="sxs-lookup"><span data-stu-id="a3ae1-126">Contract</span></span>|<span data-ttu-id="a3ae1-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3ae1-127">xs:string</span></span>|<span data-ttu-id="a3ae1-128">端點的合約。</span><span class="sxs-lookup"><span data-stu-id="a3ae1-128">The contract of the endpoint.</span></span>|  
|<span data-ttu-id="a3ae1-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a3ae1-129">AppDomain</span></span>|<span data-ttu-id="a3ae1-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3ae1-130">xs:string</span></span>|<span data-ttu-id="a3ae1-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="a3ae1-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

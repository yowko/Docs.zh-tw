---
title: 39456 - TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: d958b506e057bc0d59f954debdc9da6015bf5f1f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273095"
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="55334-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="55334-102">39456 - TrackingRecordDropped</span></span>

## <a name="properties"></a><span data-ttu-id="55334-103">屬性</span><span class="sxs-lookup"><span data-stu-id="55334-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="55334-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="55334-104">ID</span></span>|<span data-ttu-id="55334-105">39456</span><span class="sxs-lookup"><span data-stu-id="55334-105">39456</span></span>|  
|<span data-ttu-id="55334-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="55334-106">Keywords</span></span>|<span data-ttu-id="55334-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="55334-107">WFTracking</span></span>|  
|<span data-ttu-id="55334-108">層級</span><span class="sxs-lookup"><span data-stu-id="55334-108">Level</span></span>|<span data-ttu-id="55334-109">警告</span><span class="sxs-lookup"><span data-stu-id="55334-109">Warning</span></span>|  
|<span data-ttu-id="55334-110">通路</span><span class="sxs-lookup"><span data-stu-id="55334-110">Channel</span></span>|<span data-ttu-id="55334-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="55334-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="55334-112">描述</span><span class="sxs-lookup"><span data-stu-id="55334-112">Description</span></span>  

 <span data-ttu-id="55334-113">表示追蹤記錄的大小已超出 ETW 工作階段提供者所允許的最大值而丟棄追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="55334-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="55334-114">訊息</span><span class="sxs-lookup"><span data-stu-id="55334-114">Message</span></span>  

 <span data-ttu-id="55334-115">追蹤記錄 %1 的大小已超出提供者 %2 的 ETW 工作階段所允許的最大值</span><span class="sxs-lookup"><span data-stu-id="55334-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="55334-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="55334-116">Details</span></span>  
  
|<span data-ttu-id="55334-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="55334-117">Data Item Name</span></span>|<span data-ttu-id="55334-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="55334-118">Data Item Type</span></span>|<span data-ttu-id="55334-119">描述</span><span class="sxs-lookup"><span data-stu-id="55334-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="55334-120">例外狀況</span><span class="sxs-lookup"><span data-stu-id="55334-120">Exception</span></span>|<span data-ttu-id="55334-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="55334-121">xs:string</span></span>|<span data-ttu-id="55334-122">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="55334-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="55334-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="55334-123">AppDomain</span></span>|<span data-ttu-id="55334-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="55334-124">xs:string</span></span>|<span data-ttu-id="55334-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="55334-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

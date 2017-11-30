---
title: 39456 - TrackingRecordDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3e663cced42252112e1948f4907bc8c81ef941f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="fd0fc-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="fd0fc-102">39456 - TrackingRecordDropped</span></span>
## <a name="properties"></a><span data-ttu-id="fd0fc-103">屬性</span><span class="sxs-lookup"><span data-stu-id="fd0fc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fd0fc-104">ID</span><span class="sxs-lookup"><span data-stu-id="fd0fc-104">ID</span></span>|<span data-ttu-id="fd0fc-105">39456</span><span class="sxs-lookup"><span data-stu-id="fd0fc-105">39456</span></span>|  
|<span data-ttu-id="fd0fc-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="fd0fc-106">Keywords</span></span>|<span data-ttu-id="fd0fc-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="fd0fc-107">WFTracking</span></span>|  
|<span data-ttu-id="fd0fc-108">層級</span><span class="sxs-lookup"><span data-stu-id="fd0fc-108">Level</span></span>|<span data-ttu-id="fd0fc-109">警告</span><span class="sxs-lookup"><span data-stu-id="fd0fc-109">Warning</span></span>|  
|<span data-ttu-id="fd0fc-110">通道</span><span class="sxs-lookup"><span data-stu-id="fd0fc-110">Channel</span></span>|<span data-ttu-id="fd0fc-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="fd0fc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fd0fc-112">描述</span><span class="sxs-lookup"><span data-stu-id="fd0fc-112">Description</span></span>  
 <span data-ttu-id="fd0fc-113">表示追蹤記錄的大小已超出 ETW 工作階段提供者所允許的最大值而丟棄追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="fd0fc-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fd0fc-114">訊息</span><span class="sxs-lookup"><span data-stu-id="fd0fc-114">Message</span></span>  
 <span data-ttu-id="fd0fc-115">追蹤記錄 %1 的大小已超出提供者 %2 的 ETW 工作階段所允許的最大值</span><span class="sxs-lookup"><span data-stu-id="fd0fc-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="fd0fc-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fd0fc-116">Details</span></span>  
  
|<span data-ttu-id="fd0fc-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="fd0fc-117">Data Item Name</span></span>|<span data-ttu-id="fd0fc-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="fd0fc-118">Data Item Type</span></span>|<span data-ttu-id="fd0fc-119">描述</span><span class="sxs-lookup"><span data-stu-id="fd0fc-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fd0fc-120">例外狀況</span><span class="sxs-lookup"><span data-stu-id="fd0fc-120">Exception</span></span>|<span data-ttu-id="fd0fc-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="fd0fc-121">xs:string</span></span>|<span data-ttu-id="fd0fc-122">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="fd0fc-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="fd0fc-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fd0fc-123">AppDomain</span></span>|<span data-ttu-id="fd0fc-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="fd0fc-124">xs:string</span></span>|<span data-ttu-id="fd0fc-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="fd0fc-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

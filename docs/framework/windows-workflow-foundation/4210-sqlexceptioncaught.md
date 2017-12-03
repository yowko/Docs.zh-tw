---
title: 4210 - SqlExceptionCaught
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7857bb865bb8eea8fc9d1d56c1b6e69c33f7165d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="4210---sqlexceptioncaught"></a><span data-ttu-id="282ea-102">4210 - SqlExceptionCaught</span><span class="sxs-lookup"><span data-stu-id="282ea-102">4210 - SqlExceptionCaught</span></span>
## <a name="properties"></a><span data-ttu-id="282ea-103">屬性</span><span class="sxs-lookup"><span data-stu-id="282ea-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="282ea-104">ID</span><span class="sxs-lookup"><span data-stu-id="282ea-104">ID</span></span>|<span data-ttu-id="282ea-105">4210</span><span class="sxs-lookup"><span data-stu-id="282ea-105">4210</span></span>|  
|<span data-ttu-id="282ea-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="282ea-106">Keywords</span></span>|<span data-ttu-id="282ea-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="282ea-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="282ea-108">層級</span><span class="sxs-lookup"><span data-stu-id="282ea-108">Level</span></span>|<span data-ttu-id="282ea-109">警告</span><span class="sxs-lookup"><span data-stu-id="282ea-109">Warning</span></span>|  
|<span data-ttu-id="282ea-110">通道</span><span class="sxs-lookup"><span data-stu-id="282ea-110">Channel</span></span>|<span data-ttu-id="282ea-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="282ea-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="282ea-112">描述</span><span class="sxs-lookup"><span data-stu-id="282ea-112">Description</span></span>  
 <span data-ttu-id="282ea-113">表示已攔截到 SQL 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="282ea-113">Indicates a SQL exception was caught.</span></span>  
  
## <a name="message"></a><span data-ttu-id="282ea-114">訊息</span><span class="sxs-lookup"><span data-stu-id="282ea-114">Message</span></span>  
 <span data-ttu-id="282ea-115">攔截到 SQL 例外狀況編號 %1 訊息 %2。</span><span class="sxs-lookup"><span data-stu-id="282ea-115">Caught SQL Exception number %1 message %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="282ea-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="282ea-116">Details</span></span>  
  
|<span data-ttu-id="282ea-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="282ea-117">Data Item Name</span></span>|<span data-ttu-id="282ea-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="282ea-118">Data Item Type</span></span>|<span data-ttu-id="282ea-119">描述</span><span class="sxs-lookup"><span data-stu-id="282ea-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="282ea-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="282ea-120">ErrorNumber</span></span>|<span data-ttu-id="282ea-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="282ea-121">xs:string</span></span>|<span data-ttu-id="282ea-122">SQL 錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="282ea-122">The SQL error number.</span></span>|  
|<span data-ttu-id="282ea-123">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="282ea-123">ExceptionMessage</span></span>|<span data-ttu-id="282ea-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="282ea-124">xs:string</span></span>|<span data-ttu-id="282ea-125">SQL 例外狀況的訊息。</span><span class="sxs-lookup"><span data-stu-id="282ea-125">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="282ea-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="282ea-126">AppDomain</span></span>|<span data-ttu-id="282ea-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="282ea-127">xs:string</span></span>|<span data-ttu-id="282ea-128">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="282ea-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

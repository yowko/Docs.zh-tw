---
title: 4210 - SqlExceptionCaught
ms.date: 03/30/2017
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
ms.openlocfilehash: 1dab44e3fb97d74a2146f5bf992225222bc93d50
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280373"
---
# <a name="4210---sqlexceptioncaught"></a><span data-ttu-id="c400c-102">4210 - SqlExceptionCaught</span><span class="sxs-lookup"><span data-stu-id="c400c-102">4210 - SqlExceptionCaught</span></span>

## <a name="properties"></a><span data-ttu-id="c400c-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c400c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c400c-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="c400c-104">ID</span></span>|<span data-ttu-id="c400c-105">4210</span><span class="sxs-lookup"><span data-stu-id="c400c-105">4210</span></span>|  
|<span data-ttu-id="c400c-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c400c-106">Keywords</span></span>|<span data-ttu-id="c400c-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="c400c-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="c400c-108">層級</span><span class="sxs-lookup"><span data-stu-id="c400c-108">Level</span></span>|<span data-ttu-id="c400c-109">警告</span><span class="sxs-lookup"><span data-stu-id="c400c-109">Warning</span></span>|  
|<span data-ttu-id="c400c-110">通路</span><span class="sxs-lookup"><span data-stu-id="c400c-110">Channel</span></span>|<span data-ttu-id="c400c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c400c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c400c-112">描述</span><span class="sxs-lookup"><span data-stu-id="c400c-112">Description</span></span>  

 <span data-ttu-id="c400c-113">表示已攔截到 SQL 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c400c-113">Indicates a SQL exception was caught.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c400c-114">訊息</span><span class="sxs-lookup"><span data-stu-id="c400c-114">Message</span></span>  

 <span data-ttu-id="c400c-115">攔截到 SQL 例外狀況編號 %1 訊息 %2。</span><span class="sxs-lookup"><span data-stu-id="c400c-115">Caught SQL Exception number %1 message %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c400c-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c400c-116">Details</span></span>  
  
|<span data-ttu-id="c400c-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c400c-117">Data Item Name</span></span>|<span data-ttu-id="c400c-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c400c-118">Data Item Type</span></span>|<span data-ttu-id="c400c-119">描述</span><span class="sxs-lookup"><span data-stu-id="c400c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c400c-120">錯誤號碼</span><span class="sxs-lookup"><span data-stu-id="c400c-120">ErrorNumber</span></span>|<span data-ttu-id="c400c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c400c-121">xs:string</span></span>|<span data-ttu-id="c400c-122">SQL 錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="c400c-122">The SQL error number.</span></span>|  
|<span data-ttu-id="c400c-123">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="c400c-123">ExceptionMessage</span></span>|<span data-ttu-id="c400c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c400c-124">xs:string</span></span>|<span data-ttu-id="c400c-125">SQL 例外狀況的訊息。</span><span class="sxs-lookup"><span data-stu-id="c400c-125">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="c400c-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c400c-126">AppDomain</span></span>|<span data-ttu-id="c400c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c400c-127">xs:string</span></span>|<span data-ttu-id="c400c-128">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c400c-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

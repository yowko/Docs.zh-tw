---
title: 4210 - SqlExceptionCaught
ms.date: 03/30/2017
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
ms.openlocfilehash: 2493014e80e79ac2935c1bcc685147a74e48fb47
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774253"
---
# <a name="4210---sqlexceptioncaught"></a><span data-ttu-id="3688a-102">4210 - SqlExceptionCaught</span><span class="sxs-lookup"><span data-stu-id="3688a-102">4210 - SqlExceptionCaught</span></span>
## <a name="properties"></a><span data-ttu-id="3688a-103">屬性</span><span class="sxs-lookup"><span data-stu-id="3688a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3688a-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="3688a-104">ID</span></span>|<span data-ttu-id="3688a-105">4210</span><span class="sxs-lookup"><span data-stu-id="3688a-105">4210</span></span>|  
|<span data-ttu-id="3688a-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="3688a-106">Keywords</span></span>|<span data-ttu-id="3688a-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="3688a-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="3688a-108">層級</span><span class="sxs-lookup"><span data-stu-id="3688a-108">Level</span></span>|<span data-ttu-id="3688a-109">警告</span><span class="sxs-lookup"><span data-stu-id="3688a-109">Warning</span></span>|  
|<span data-ttu-id="3688a-110">通道</span><span class="sxs-lookup"><span data-stu-id="3688a-110">Channel</span></span>|<span data-ttu-id="3688a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3688a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3688a-112">描述</span><span class="sxs-lookup"><span data-stu-id="3688a-112">Description</span></span>  
 <span data-ttu-id="3688a-113">表示已攔截到 SQL 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3688a-113">Indicates a SQL exception was caught.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3688a-114">訊息</span><span class="sxs-lookup"><span data-stu-id="3688a-114">Message</span></span>  
 <span data-ttu-id="3688a-115">攔截到 SQL 例外狀況編號 %1 訊息 %2。</span><span class="sxs-lookup"><span data-stu-id="3688a-115">Caught SQL Exception number %1 message %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3688a-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3688a-116">Details</span></span>  
  
|<span data-ttu-id="3688a-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="3688a-117">Data Item Name</span></span>|<span data-ttu-id="3688a-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="3688a-118">Data Item Type</span></span>|<span data-ttu-id="3688a-119">描述</span><span class="sxs-lookup"><span data-stu-id="3688a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3688a-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="3688a-120">ErrorNumber</span></span>|<span data-ttu-id="3688a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="3688a-121">xs:string</span></span>|<span data-ttu-id="3688a-122">SQL 錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="3688a-122">The SQL error number.</span></span>|  
|<span data-ttu-id="3688a-123">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="3688a-123">ExceptionMessage</span></span>|<span data-ttu-id="3688a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3688a-124">xs:string</span></span>|<span data-ttu-id="3688a-125">SQL 例外狀況的訊息。</span><span class="sxs-lookup"><span data-stu-id="3688a-125">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="3688a-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3688a-126">AppDomain</span></span>|<span data-ttu-id="3688a-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="3688a-127">xs:string</span></span>|<span data-ttu-id="3688a-128">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="3688a-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

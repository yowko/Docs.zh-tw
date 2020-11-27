---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 61605d666911cce277bcebbb0a2f803e9a5dcfeb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261302"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="aa7d1-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="aa7d1-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>

## <a name="properties"></a><span data-ttu-id="aa7d1-103">屬性</span><span class="sxs-lookup"><span data-stu-id="aa7d1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aa7d1-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="aa7d1-104">ID</span></span>|<span data-ttu-id="aa7d1-105">3550</span><span class="sxs-lookup"><span data-stu-id="aa7d1-105">3550</span></span>|  
|<span data-ttu-id="aa7d1-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="aa7d1-106">Keywords</span></span>|<span data-ttu-id="aa7d1-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="aa7d1-107">WFServices</span></span>|  
|<span data-ttu-id="aa7d1-108">層級</span><span class="sxs-lookup"><span data-stu-id="aa7d1-108">Level</span></span>|<span data-ttu-id="aa7d1-109">資訊</span><span class="sxs-lookup"><span data-stu-id="aa7d1-109">Information</span></span>|  
|<span data-ttu-id="aa7d1-110">通路</span><span class="sxs-lookup"><span data-stu-id="aa7d1-110">Channel</span></span>|<span data-ttu-id="aa7d1-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="aa7d1-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aa7d1-112">描述</span><span class="sxs-lookup"><span data-stu-id="aa7d1-112">Description</span></span>  

 <span data-ttu-id="aa7d1-113">表示緩衝接收已失敗。</span><span class="sxs-lookup"><span data-stu-id="aa7d1-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="aa7d1-114">當服務執行個體準備好處理這個特定作業時，就會再次嘗試此作業。</span><span class="sxs-lookup"><span data-stu-id="aa7d1-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aa7d1-115">訊息</span><span class="sxs-lookup"><span data-stu-id="aa7d1-115">Message</span></span>  

 <span data-ttu-id="aa7d1-116">目前無法執行作業 '%1'。</span><span class="sxs-lookup"><span data-stu-id="aa7d1-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="aa7d1-117">將在服務執行個體準備就緒可以處理這個特定作業時，再次嘗試。</span><span class="sxs-lookup"><span data-stu-id="aa7d1-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aa7d1-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aa7d1-118">Details</span></span>  
  
|<span data-ttu-id="aa7d1-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="aa7d1-119">Data Item Name</span></span>|<span data-ttu-id="aa7d1-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="aa7d1-120">Data Item Type</span></span>|<span data-ttu-id="aa7d1-121">描述</span><span class="sxs-lookup"><span data-stu-id="aa7d1-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aa7d1-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="aa7d1-122">OperationName</span></span>|<span data-ttu-id="aa7d1-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="aa7d1-123">xs:string</span></span>|<span data-ttu-id="aa7d1-124">作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="aa7d1-124">The name of the operation.</span></span>|  
|<span data-ttu-id="aa7d1-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="aa7d1-125">AppDomain</span></span>|<span data-ttu-id="aa7d1-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="aa7d1-126">xs:string</span></span>|<span data-ttu-id="aa7d1-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="aa7d1-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

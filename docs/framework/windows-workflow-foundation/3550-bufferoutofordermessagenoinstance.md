---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 1af943e23aa643c6614b946175c0b1854a7ceb62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755580"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="2fa81-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="2fa81-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="2fa81-103">屬性</span><span class="sxs-lookup"><span data-stu-id="2fa81-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2fa81-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="2fa81-104">ID</span></span>|<span data-ttu-id="2fa81-105">3550</span><span class="sxs-lookup"><span data-stu-id="2fa81-105">3550</span></span>|  
|<span data-ttu-id="2fa81-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="2fa81-106">Keywords</span></span>|<span data-ttu-id="2fa81-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="2fa81-107">WFServices</span></span>|  
|<span data-ttu-id="2fa81-108">層級</span><span class="sxs-lookup"><span data-stu-id="2fa81-108">Level</span></span>|<span data-ttu-id="2fa81-109">資訊</span><span class="sxs-lookup"><span data-stu-id="2fa81-109">Information</span></span>|  
|<span data-ttu-id="2fa81-110">通道</span><span class="sxs-lookup"><span data-stu-id="2fa81-110">Channel</span></span>|<span data-ttu-id="2fa81-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="2fa81-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2fa81-112">描述</span><span class="sxs-lookup"><span data-stu-id="2fa81-112">Description</span></span>  
 <span data-ttu-id="2fa81-113">表示緩衝接收已失敗。</span><span class="sxs-lookup"><span data-stu-id="2fa81-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="2fa81-114">當服務執行個體準備好處理這個特定作業時，就會再次嘗試此作業。</span><span class="sxs-lookup"><span data-stu-id="2fa81-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2fa81-115">訊息</span><span class="sxs-lookup"><span data-stu-id="2fa81-115">Message</span></span>  
 <span data-ttu-id="2fa81-116">目前無法執行作業 '%1'。</span><span class="sxs-lookup"><span data-stu-id="2fa81-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="2fa81-117">將在服務執行個體準備就緒可以處理這個特定作業時，再次嘗試。</span><span class="sxs-lookup"><span data-stu-id="2fa81-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2fa81-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2fa81-118">Details</span></span>  
  
|<span data-ttu-id="2fa81-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="2fa81-119">Data Item Name</span></span>|<span data-ttu-id="2fa81-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="2fa81-120">Data Item Type</span></span>|<span data-ttu-id="2fa81-121">描述</span><span class="sxs-lookup"><span data-stu-id="2fa81-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2fa81-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="2fa81-122">OperationName</span></span>|<span data-ttu-id="2fa81-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="2fa81-123">xs:string</span></span>|<span data-ttu-id="2fa81-124">作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="2fa81-124">The name of the operation.</span></span>|  
|<span data-ttu-id="2fa81-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2fa81-125">AppDomain</span></span>|<span data-ttu-id="2fa81-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="2fa81-126">xs:string</span></span>|<span data-ttu-id="2fa81-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="2fa81-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 1af943e23aa643c6614b946175c0b1854a7ceb62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511587"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="9fec1-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="9fec1-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="9fec1-103">屬性</span><span class="sxs-lookup"><span data-stu-id="9fec1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9fec1-104">ID</span><span class="sxs-lookup"><span data-stu-id="9fec1-104">ID</span></span>|<span data-ttu-id="9fec1-105">3550</span><span class="sxs-lookup"><span data-stu-id="9fec1-105">3550</span></span>|  
|<span data-ttu-id="9fec1-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="9fec1-106">Keywords</span></span>|<span data-ttu-id="9fec1-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="9fec1-107">WFServices</span></span>|  
|<span data-ttu-id="9fec1-108">層級</span><span class="sxs-lookup"><span data-stu-id="9fec1-108">Level</span></span>|<span data-ttu-id="9fec1-109">資訊</span><span class="sxs-lookup"><span data-stu-id="9fec1-109">Information</span></span>|  
|<span data-ttu-id="9fec1-110">通道</span><span class="sxs-lookup"><span data-stu-id="9fec1-110">Channel</span></span>|<span data-ttu-id="9fec1-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="9fec1-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9fec1-112">描述</span><span class="sxs-lookup"><span data-stu-id="9fec1-112">Description</span></span>  
 <span data-ttu-id="9fec1-113">表示緩衝接收已失敗。</span><span class="sxs-lookup"><span data-stu-id="9fec1-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="9fec1-114">當服務執行個體準備好處理這個特定作業時，就會再次嘗試此作業。</span><span class="sxs-lookup"><span data-stu-id="9fec1-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9fec1-115">訊息</span><span class="sxs-lookup"><span data-stu-id="9fec1-115">Message</span></span>  
 <span data-ttu-id="9fec1-116">目前無法執行作業 '%1'。</span><span class="sxs-lookup"><span data-stu-id="9fec1-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="9fec1-117">將在服務執行個體準備就緒可以處理這個特定作業時，再次嘗試。</span><span class="sxs-lookup"><span data-stu-id="9fec1-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9fec1-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9fec1-118">Details</span></span>  
  
|<span data-ttu-id="9fec1-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="9fec1-119">Data Item Name</span></span>|<span data-ttu-id="9fec1-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="9fec1-120">Data Item Type</span></span>|<span data-ttu-id="9fec1-121">描述</span><span class="sxs-lookup"><span data-stu-id="9fec1-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9fec1-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="9fec1-122">OperationName</span></span>|<span data-ttu-id="9fec1-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="9fec1-123">xs:string</span></span>|<span data-ttu-id="9fec1-124">作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="9fec1-124">The name of the operation.</span></span>|  
|<span data-ttu-id="9fec1-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9fec1-125">AppDomain</span></span>|<span data-ttu-id="9fec1-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="9fec1-126">xs:string</span></span>|<span data-ttu-id="9fec1-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="9fec1-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 1037 - RuntimeTransactionComplete
ms.date: 03/30/2017
ms.assetid: 2c8c31e0-42a9-4f46-865b-2da9ab16a0ba
ms.openlocfilehash: ad05151a1497ea4b31e0fe33fe2983c1f145f224
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294244"
---
# <a name="1037---runtimetransactioncomplete"></a><span data-ttu-id="b226e-102">1037 - RuntimeTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="b226e-102">1037 - RuntimeTransactionComplete</span></span>

## <a name="properties"></a><span data-ttu-id="b226e-103">屬性</span><span class="sxs-lookup"><span data-stu-id="b226e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b226e-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="b226e-104">ID</span></span>|<span data-ttu-id="b226e-105">1037</span><span class="sxs-lookup"><span data-stu-id="b226e-105">1037</span></span>|  
|<span data-ttu-id="b226e-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="b226e-106">Keywords</span></span>|<span data-ttu-id="b226e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b226e-107">WFRuntime</span></span>|  
|<span data-ttu-id="b226e-108">層級</span><span class="sxs-lookup"><span data-stu-id="b226e-108">Level</span></span>|<span data-ttu-id="b226e-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="b226e-109">Verbose</span></span>|  
|<span data-ttu-id="b226e-110">通路</span><span class="sxs-lookup"><span data-stu-id="b226e-110">Channel</span></span>|<span data-ttu-id="b226e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="b226e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b226e-112">描述</span><span class="sxs-lookup"><span data-stu-id="b226e-112">Description</span></span>  

 <span data-ttu-id="b226e-113">表示執行階段異動已完成。</span><span class="sxs-lookup"><span data-stu-id="b226e-113">Indicates the runtime transaction has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b226e-114">訊息</span><span class="sxs-lookup"><span data-stu-id="b226e-114">Message</span></span>  

 <span data-ttu-id="b226e-115">執行階段異動已完成，狀態為 '%1'。</span><span class="sxs-lookup"><span data-stu-id="b226e-115">The runtime transaction has completed with the state '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b226e-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b226e-116">Details</span></span>  
  
|<span data-ttu-id="b226e-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="b226e-117">Data Item Name</span></span>|<span data-ttu-id="b226e-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="b226e-118">Data Item Type</span></span>|<span data-ttu-id="b226e-119">描述</span><span class="sxs-lookup"><span data-stu-id="b226e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b226e-120">State</span><span class="sxs-lookup"><span data-stu-id="b226e-120">State</span></span>|<span data-ttu-id="b226e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="b226e-121">xs:string</span></span>|<span data-ttu-id="b226e-122">異動的狀態。</span><span class="sxs-lookup"><span data-stu-id="b226e-122">The state of the transaction.</span></span>|  
|<span data-ttu-id="b226e-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b226e-123">AppDomain</span></span>|<span data-ttu-id="b226e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="b226e-124">xs:string</span></span>|<span data-ttu-id="b226e-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="b226e-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

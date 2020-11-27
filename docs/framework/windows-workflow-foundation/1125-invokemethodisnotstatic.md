---
title: 1125 - InvokeMethodIsNotStatic
ms.date: 03/30/2017
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
ms.openlocfilehash: 0405b4e1207db5c056fbd478b98c408258daf0c3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294205"
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="e5511-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="e5511-102">1125 - InvokeMethodIsNotStatic</span></span>

## <a name="properties"></a><span data-ttu-id="e5511-103">屬性</span><span class="sxs-lookup"><span data-stu-id="e5511-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e5511-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="e5511-104">ID</span></span>|<span data-ttu-id="e5511-105">1125</span><span class="sxs-lookup"><span data-stu-id="e5511-105">1125</span></span>|  
|<span data-ttu-id="e5511-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e5511-106">Keywords</span></span>|<span data-ttu-id="e5511-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e5511-107">WFRuntime</span></span>|  
|<span data-ttu-id="e5511-108">層級</span><span class="sxs-lookup"><span data-stu-id="e5511-108">Level</span></span>|<span data-ttu-id="e5511-109">資訊</span><span class="sxs-lookup"><span data-stu-id="e5511-109">Information</span></span>|  
|<span data-ttu-id="e5511-110">通路</span><span class="sxs-lookup"><span data-stu-id="e5511-110">Channel</span></span>|<span data-ttu-id="e5511-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e5511-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e5511-112">描述</span><span class="sxs-lookup"><span data-stu-id="e5511-112">Description</span></span>  

 <span data-ttu-id="e5511-113">在 CacheMetadata 步驟期間，InvokeMethod 活動指出要叫用的方法不是靜態的。</span><span class="sxs-lookup"><span data-stu-id="e5511-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e5511-114">訊息</span><span class="sxs-lookup"><span data-stu-id="e5511-114">Message</span></span>  

 <span data-ttu-id="e5511-115">InvokeMethod '%1' - 方法不是靜態方法。</span><span class="sxs-lookup"><span data-stu-id="e5511-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e5511-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e5511-116">Details</span></span>  
  
|<span data-ttu-id="e5511-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="e5511-117">Data Item Name</span></span>|<span data-ttu-id="e5511-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="e5511-118">Data Item Type</span></span>|<span data-ttu-id="e5511-119">描述</span><span class="sxs-lookup"><span data-stu-id="e5511-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e5511-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="e5511-120">InvokeMethod</span></span>|<span data-ttu-id="e5511-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e5511-121">xs:string</span></span>|<span data-ttu-id="e5511-122">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="e5511-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="e5511-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e5511-123">AppDomain</span></span>|<span data-ttu-id="e5511-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e5511-124">xs:string</span></span>|<span data-ttu-id="e5511-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="e5511-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

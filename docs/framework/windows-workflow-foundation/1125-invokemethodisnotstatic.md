---
title: 1125 - InvokeMethodIsNotStatic
ms.date: 03/30/2017
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
ms.openlocfilehash: 692c5e56dac0a69ab5705acd284f048391145641
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511939"
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="9365c-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="9365c-102">1125 - InvokeMethodIsNotStatic</span></span>
## <a name="properties"></a><span data-ttu-id="9365c-103">屬性</span><span class="sxs-lookup"><span data-stu-id="9365c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9365c-104">ID</span><span class="sxs-lookup"><span data-stu-id="9365c-104">ID</span></span>|<span data-ttu-id="9365c-105">1125</span><span class="sxs-lookup"><span data-stu-id="9365c-105">1125</span></span>|  
|<span data-ttu-id="9365c-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="9365c-106">Keywords</span></span>|<span data-ttu-id="9365c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9365c-107">WFRuntime</span></span>|  
|<span data-ttu-id="9365c-108">層級</span><span class="sxs-lookup"><span data-stu-id="9365c-108">Level</span></span>|<span data-ttu-id="9365c-109">資訊</span><span class="sxs-lookup"><span data-stu-id="9365c-109">Information</span></span>|  
|<span data-ttu-id="9365c-110">通道</span><span class="sxs-lookup"><span data-stu-id="9365c-110">Channel</span></span>|<span data-ttu-id="9365c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9365c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9365c-112">描述</span><span class="sxs-lookup"><span data-stu-id="9365c-112">Description</span></span>  
 <span data-ttu-id="9365c-113">在 CacheMetadata 步驟期間，InvokeMethod 活動指出要叫用的方法不是靜態的。</span><span class="sxs-lookup"><span data-stu-id="9365c-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9365c-114">訊息</span><span class="sxs-lookup"><span data-stu-id="9365c-114">Message</span></span>  
 <span data-ttu-id="9365c-115">InvokeMethod '%1' - 方法不是靜態方法。</span><span class="sxs-lookup"><span data-stu-id="9365c-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9365c-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9365c-116">Details</span></span>  
  
|<span data-ttu-id="9365c-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="9365c-117">Data Item Name</span></span>|<span data-ttu-id="9365c-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="9365c-118">Data Item Type</span></span>|<span data-ttu-id="9365c-119">描述</span><span class="sxs-lookup"><span data-stu-id="9365c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9365c-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="9365c-120">InvokeMethod</span></span>|<span data-ttu-id="9365c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="9365c-121">xs:string</span></span>|<span data-ttu-id="9365c-122">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="9365c-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="9365c-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9365c-123">AppDomain</span></span>|<span data-ttu-id="9365c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="9365c-124">xs:string</span></span>|<span data-ttu-id="9365c-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="9365c-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

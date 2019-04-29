---
title: 4206 - UnlockInstanceException
ms.date: 03/30/2017
ms.assetid: 5a46dc5f-d517-4135-8905-25a42f01206b
ms.openlocfilehash: 3c981888b491f2797a431c2103ba3f5f0bd17046
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774318"
---
# <a name="4206---unlockinstanceexception"></a><span data-ttu-id="fdb5a-102">4206 - UnlockInstanceException</span><span class="sxs-lookup"><span data-stu-id="fdb5a-102">4206 - UnlockInstanceException</span></span>
## <a name="properties"></a><span data-ttu-id="fdb5a-103">屬性</span><span class="sxs-lookup"><span data-stu-id="fdb5a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fdb5a-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="fdb5a-104">ID</span></span>|<span data-ttu-id="fdb5a-105">4206</span><span class="sxs-lookup"><span data-stu-id="fdb5a-105">4206</span></span>|  
|<span data-ttu-id="fdb5a-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="fdb5a-106">Keywords</span></span>|<span data-ttu-id="fdb5a-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="fdb5a-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="fdb5a-108">層級</span><span class="sxs-lookup"><span data-stu-id="fdb5a-108">Level</span></span>|<span data-ttu-id="fdb5a-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="fdb5a-109">Error</span></span>|  
|<span data-ttu-id="fdb5a-110">通道</span><span class="sxs-lookup"><span data-stu-id="fdb5a-110">Channel</span></span>|<span data-ttu-id="fdb5a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="fdb5a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fdb5a-112">描述</span><span class="sxs-lookup"><span data-stu-id="fdb5a-112">Description</span></span>  
 <span data-ttu-id="fdb5a-113">表示在嘗試解除鎖定執行個體時，發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fdb5a-113">Indicates an exception was encountered while trying to unlock an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fdb5a-114">訊息</span><span class="sxs-lookup"><span data-stu-id="fdb5a-114">Message</span></span>  
 <span data-ttu-id="fdb5a-115">嘗試解除鎖定執行個體時，發生例外狀況 %1。</span><span class="sxs-lookup"><span data-stu-id="fdb5a-115">Encountered exception %1 while attempting to unlock instance.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fdb5a-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fdb5a-116">Details</span></span>  
  
|<span data-ttu-id="fdb5a-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="fdb5a-117">Data Item Name</span></span>|<span data-ttu-id="fdb5a-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="fdb5a-118">Data Item Type</span></span>|<span data-ttu-id="fdb5a-119">描述</span><span class="sxs-lookup"><span data-stu-id="fdb5a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fdb5a-120">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="fdb5a-120">ExceptionMessage</span></span>|<span data-ttu-id="fdb5a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="fdb5a-121">xs:string</span></span>|<span data-ttu-id="fdb5a-122">SQL 例外狀況的訊息。</span><span class="sxs-lookup"><span data-stu-id="fdb5a-122">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="fdb5a-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fdb5a-123">AppDomain</span></span>|<span data-ttu-id="fdb5a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="fdb5a-124">xs:string</span></span>|<span data-ttu-id="fdb5a-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="fdb5a-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 4207 - MaximumRetriesExceededForSqlCommand
ms.date: 03/30/2017
ms.assetid: 8c8bee26-9ad4-4e01-bd16-0e1fd510fb6b
ms.openlocfilehash: b763e087d8ead2bcc0fadd1d0223ae1bd58c9fd9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774305"
---
# <a name="4207---maximumretriesexceededforsqlcommand"></a><span data-ttu-id="29e37-102">4207 - MaximumRetriesExceededForSqlCommand</span><span class="sxs-lookup"><span data-stu-id="29e37-102">4207 - MaximumRetriesExceededForSqlCommand</span></span>
## <a name="properties"></a><span data-ttu-id="29e37-103">屬性</span><span class="sxs-lookup"><span data-stu-id="29e37-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29e37-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="29e37-104">ID</span></span>|<span data-ttu-id="29e37-105">4207</span><span class="sxs-lookup"><span data-stu-id="29e37-105">4207</span></span>|  
|<span data-ttu-id="29e37-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="29e37-106">Keywords</span></span>|<span data-ttu-id="29e37-107">Quota、WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="29e37-107">Quota, WFInstanceStore</span></span>|  
|<span data-ttu-id="29e37-108">層級</span><span class="sxs-lookup"><span data-stu-id="29e37-108">Level</span></span>|<span data-ttu-id="29e37-109">資訊</span><span class="sxs-lookup"><span data-stu-id="29e37-109">Information</span></span>|  
|<span data-ttu-id="29e37-110">通道</span><span class="sxs-lookup"><span data-stu-id="29e37-110">Channel</span></span>|<span data-ttu-id="29e37-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="29e37-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="29e37-112">描述</span><span class="sxs-lookup"><span data-stu-id="29e37-112">Description</span></span>  
 <span data-ttu-id="29e37-113">表示 SQL 提供者要放棄重試 SQL 命令，因為已經執行了重試次數上限。</span><span class="sxs-lookup"><span data-stu-id="29e37-113">Indicates SQL provider is giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="29e37-114">訊息</span><span class="sxs-lookup"><span data-stu-id="29e37-114">Message</span></span>  
 <span data-ttu-id="29e37-115">放棄重試 SQL 命令，因為已經執行了重試次數上限。</span><span class="sxs-lookup"><span data-stu-id="29e37-115">Giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="details"></a><span data-ttu-id="29e37-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="29e37-116">Details</span></span>  
  
|<span data-ttu-id="29e37-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="29e37-117">Data Item Name</span></span>|<span data-ttu-id="29e37-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="29e37-118">Data Item Type</span></span>|<span data-ttu-id="29e37-119">描述</span><span class="sxs-lookup"><span data-stu-id="29e37-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="29e37-120">AppDomain</span><span class="sxs-lookup"><span data-stu-id="29e37-120">AppDomain</span></span>|<span data-ttu-id="29e37-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="29e37-121">xs:string</span></span>|<span data-ttu-id="29e37-122">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="29e37-122">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

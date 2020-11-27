---
title: 4201 - EndSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
ms.openlocfilehash: 0d6326889077e36ad49aa6267ae7285849c6818d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275862"
---
# <a name="4201---endsqlcommandexecute"></a><span data-ttu-id="eb691-102">4201 - EndSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="eb691-102">4201 - EndSqlCommandExecute</span></span>

## <a name="properties"></a><span data-ttu-id="eb691-103">屬性</span><span class="sxs-lookup"><span data-stu-id="eb691-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eb691-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="eb691-104">ID</span></span>|<span data-ttu-id="eb691-105">4201</span><span class="sxs-lookup"><span data-stu-id="eb691-105">4201</span></span>|  
|<span data-ttu-id="eb691-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="eb691-106">Keywords</span></span>|<span data-ttu-id="eb691-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="eb691-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="eb691-108">層級</span><span class="sxs-lookup"><span data-stu-id="eb691-108">Level</span></span>|<span data-ttu-id="eb691-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="eb691-109">Verbose</span></span>|  
|<span data-ttu-id="eb691-110">通路</span><span class="sxs-lookup"><span data-stu-id="eb691-110">Channel</span></span>|<span data-ttu-id="eb691-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="eb691-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="eb691-112">描述</span><span class="sxs-lookup"><span data-stu-id="eb691-112">Description</span></span>  

 <span data-ttu-id="eb691-113">表示 SQL 命令已完成執行。</span><span class="sxs-lookup"><span data-stu-id="eb691-113">Indicates a SQL command has finished executing.</span></span>  
  
## <a name="message"></a><span data-ttu-id="eb691-114">訊息</span><span class="sxs-lookup"><span data-stu-id="eb691-114">Message</span></span>  

 <span data-ttu-id="eb691-115">結束 SQL 命令執行：%1</span><span class="sxs-lookup"><span data-stu-id="eb691-115">End SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="eb691-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="eb691-116">Details</span></span>  
  
|<span data-ttu-id="eb691-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="eb691-117">Data Item Name</span></span>|<span data-ttu-id="eb691-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="eb691-118">Data Item Type</span></span>|<span data-ttu-id="eb691-119">描述</span><span class="sxs-lookup"><span data-stu-id="eb691-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="eb691-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="eb691-120">SqlCommand</span></span>|<span data-ttu-id="eb691-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="eb691-121">xs:string</span></span>|<span data-ttu-id="eb691-122">所執行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="eb691-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="eb691-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="eb691-123">AppDomain</span></span>|<span data-ttu-id="eb691-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="eb691-124">xs:string</span></span>|<span data-ttu-id="eb691-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="eb691-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

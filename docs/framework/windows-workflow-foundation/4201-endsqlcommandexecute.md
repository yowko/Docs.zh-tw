---
title: 4201 - EndSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
ms.openlocfilehash: 75c1cdd10aca6b177911bd9d2f51468016eb9e15
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774357"
---
# <a name="4201---endsqlcommandexecute"></a><span data-ttu-id="f0ccb-102">4201 - EndSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="f0ccb-102">4201 - EndSqlCommandExecute</span></span>
## <a name="properties"></a><span data-ttu-id="f0ccb-103">屬性</span><span class="sxs-lookup"><span data-stu-id="f0ccb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f0ccb-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="f0ccb-104">ID</span></span>|<span data-ttu-id="f0ccb-105">4201</span><span class="sxs-lookup"><span data-stu-id="f0ccb-105">4201</span></span>|  
|<span data-ttu-id="f0ccb-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="f0ccb-106">Keywords</span></span>|<span data-ttu-id="f0ccb-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="f0ccb-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="f0ccb-108">層級</span><span class="sxs-lookup"><span data-stu-id="f0ccb-108">Level</span></span>|<span data-ttu-id="f0ccb-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="f0ccb-109">Verbose</span></span>|  
|<span data-ttu-id="f0ccb-110">通道</span><span class="sxs-lookup"><span data-stu-id="f0ccb-110">Channel</span></span>|<span data-ttu-id="f0ccb-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f0ccb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f0ccb-112">描述</span><span class="sxs-lookup"><span data-stu-id="f0ccb-112">Description</span></span>  
 <span data-ttu-id="f0ccb-113">表示 SQL 命令已完成執行。</span><span class="sxs-lookup"><span data-stu-id="f0ccb-113">Indicates a SQL command has finished executing.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f0ccb-114">訊息</span><span class="sxs-lookup"><span data-stu-id="f0ccb-114">Message</span></span>  
 <span data-ttu-id="f0ccb-115">結束 SQL 命令執行：%1</span><span class="sxs-lookup"><span data-stu-id="f0ccb-115">End SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="f0ccb-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f0ccb-116">Details</span></span>  
  
|<span data-ttu-id="f0ccb-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="f0ccb-117">Data Item Name</span></span>|<span data-ttu-id="f0ccb-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="f0ccb-118">Data Item Type</span></span>|<span data-ttu-id="f0ccb-119">描述</span><span class="sxs-lookup"><span data-stu-id="f0ccb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f0ccb-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="f0ccb-120">SqlCommand</span></span>|<span data-ttu-id="f0ccb-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f0ccb-121">xs:string</span></span>|<span data-ttu-id="f0ccb-122">所執行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="f0ccb-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="f0ccb-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f0ccb-123">AppDomain</span></span>|<span data-ttu-id="f0ccb-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f0ccb-124">xs:string</span></span>|<span data-ttu-id="f0ccb-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="f0ccb-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted
ms.date: 03/30/2017
ms.assetid: 19e9a660-25f3-4332-b716-a12a59f2cbbb
ms.openlocfilehash: 46d71979e7b6bfcccc27064fd6fee626ea71dc1c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242574"
---
# <a name="4806---discoverymessagewithinvalidrelatestooroperationcompleted"></a><span data-ttu-id="09ce2-102">4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="09ce2-102">4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="09ce2-103">屬性</span><span class="sxs-lookup"><span data-stu-id="09ce2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="09ce2-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="09ce2-104">ID</span></span>|<span data-ttu-id="09ce2-105">4806</span><span class="sxs-lookup"><span data-stu-id="09ce2-105">4806</span></span>|  
|<span data-ttu-id="09ce2-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="09ce2-106">Keywords</span></span>|<span data-ttu-id="09ce2-107">探索</span><span class="sxs-lookup"><span data-stu-id="09ce2-107">Discovery</span></span>|  
|<span data-ttu-id="09ce2-108">層級</span><span class="sxs-lookup"><span data-stu-id="09ce2-108">Level</span></span>|<span data-ttu-id="09ce2-109">警告</span><span class="sxs-lookup"><span data-stu-id="09ce2-109">Warning</span></span>|  
|<span data-ttu-id="09ce2-110">通路</span><span class="sxs-lookup"><span data-stu-id="09ce2-110">Channel</span></span>|<span data-ttu-id="09ce2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="09ce2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="09ce2-112">描述</span><span class="sxs-lookup"><span data-stu-id="09ce2-112">Description</span></span>  

 <span data-ttu-id="09ce2-113">當對應的作業已完成，或是 relatesTo 值無效，導致探索訊息已由 DiscoveryClient 丟棄時，就會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="09ce2-113">This event is emitted when the discovery message was dropped by the DiscoveryClient because either the corresponding operation was completed or the relatesTo value is invalid.</span></span>  
  
## <a name="message"></a><span data-ttu-id="09ce2-114">訊息</span><span class="sxs-lookup"><span data-stu-id="09ce2-114">Message</span></span>  

 <span data-ttu-id="09ce2-115">messageId='%2' 且 relatesTo='%3' 的 %1 訊息已由 DiscoveryClient 丟棄，因為對應的 %4 作業已完成，或是 relatesTo 值無效。</span><span class="sxs-lookup"><span data-stu-id="09ce2-115">A %1 message with messageId='%2' and relatesTo='%3' was dropped by the DiscoveryClient because either the corresponding %4 operation was completed or the relatesTo value is invalid.</span></span>  
  
## <a name="details"></a><span data-ttu-id="09ce2-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="09ce2-116">Details</span></span>

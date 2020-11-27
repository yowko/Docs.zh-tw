---
title: 4811 - DiscoveryMessageWithNullRelatesTo
ms.date: 03/30/2017
ms.assetid: dab901e8-a2b3-41c1-a76b-bcd8b3c7c29a
ms.openlocfilehash: 2f2eeee50ed6925ab1f3762dbdd898c375756b7e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267416"
---
# <a name="4811---discoverymessagewithnullrelatesto"></a><span data-ttu-id="46a22-102">4811 - DiscoveryMessageWithNullRelatesTo</span><span class="sxs-lookup"><span data-stu-id="46a22-102">4811 - DiscoveryMessageWithNullRelatesTo</span></span>

## <a name="properties"></a><span data-ttu-id="46a22-103">屬性</span><span class="sxs-lookup"><span data-stu-id="46a22-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46a22-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="46a22-104">ID</span></span>|<span data-ttu-id="46a22-105">4811</span><span class="sxs-lookup"><span data-stu-id="46a22-105">4811</span></span>|  
|<span data-ttu-id="46a22-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="46a22-106">Keywords</span></span>|<span data-ttu-id="46a22-107">探索</span><span class="sxs-lookup"><span data-stu-id="46a22-107">Discovery</span></span>|  
|<span data-ttu-id="46a22-108">層級</span><span class="sxs-lookup"><span data-stu-id="46a22-108">Level</span></span>|<span data-ttu-id="46a22-109">警告</span><span class="sxs-lookup"><span data-stu-id="46a22-109">Warning</span></span>|  
|<span data-ttu-id="46a22-110">通路</span><span class="sxs-lookup"><span data-stu-id="46a22-110">Channel</span></span>|<span data-ttu-id="46a22-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="46a22-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="46a22-112">描述</span><span class="sxs-lookup"><span data-stu-id="46a22-112">Description</span></span>  

 <span data-ttu-id="46a22-113">當探索訊息因為訊息標頭未包含必要的 RelatesTo 屬性而遭 DiscoveryClient 丟棄時，會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="46a22-113">This event is emitted when the discovery message was dropped by the DiscoveryClient because the message header did not contain the required RelatesTo property.</span></span>  
  
## <a name="message"></a><span data-ttu-id="46a22-114">訊息</span><span class="sxs-lookup"><span data-stu-id="46a22-114">Message</span></span>  

 <span data-ttu-id="46a22-115">messageId='%2' 的 %1 訊息已遭 DiscoveryClient 丟棄，因為訊息標頭未包含必要的 RelatesTo 屬性。</span><span class="sxs-lookup"><span data-stu-id="46a22-115">A %1 message with messageId='%2' was dropped by the DiscoveryClient because the message header did not contain the required RelatesTo property.</span></span>  
  
## <a name="details"></a><span data-ttu-id="46a22-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="46a22-116">Details</span></span>

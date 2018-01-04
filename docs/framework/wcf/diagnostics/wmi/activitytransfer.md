---
title: ActivityTransfer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f3db50a32fabc117c79eef5ac086a7798f86ed3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="activitytransfer"></a><span data-ttu-id="feb21-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="feb21-102">ActivityTransfer</span></span>
<span data-ttu-id="feb21-103">活動傳輸事件</span><span class="sxs-lookup"><span data-stu-id="feb21-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feb21-104">語法</span><span class="sxs-lookup"><span data-stu-id="feb21-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="feb21-105">方法</span><span class="sxs-lookup"><span data-stu-id="feb21-105">Methods</span></span>  
 <span data-ttu-id="feb21-106">ActivityTransfer 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="feb21-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="feb21-107">屬性</span><span class="sxs-lookup"><span data-stu-id="feb21-107">Properties</span></span>  
 <span data-ttu-id="feb21-108">ActivityTransfer 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="feb21-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="feb21-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="feb21-109">ActivityID</span></span>  
  
-   <span data-ttu-id="feb21-110">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="feb21-110">Data type: object</span></span>  
    <span data-ttu-id="feb21-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="feb21-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="feb21-112">活動識別碼</span><span class="sxs-lookup"><span data-stu-id="feb21-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="feb21-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="feb21-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="feb21-114">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="feb21-114">Data type: object</span></span>  
    <span data-ttu-id="feb21-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="feb21-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="feb21-116">相關活動識別碼</span><span class="sxs-lookup"><span data-stu-id="feb21-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feb21-117">需求</span><span class="sxs-lookup"><span data-stu-id="feb21-117">Requirements</span></span>  
  
|<span data-ttu-id="feb21-118">MOF</span><span class="sxs-lookup"><span data-stu-id="feb21-118">MOF</span></span>|<span data-ttu-id="feb21-119">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="feb21-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="feb21-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="feb21-120">Namespace</span></span>|<span data-ttu-id="feb21-121">於 root\ServiceModel 中定義。</span><span class="sxs-lookup"><span data-stu-id="feb21-121">Defined in root\ServiceModel.</span></span>|

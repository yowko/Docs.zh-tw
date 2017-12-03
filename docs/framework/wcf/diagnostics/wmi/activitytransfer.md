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
ms.openlocfilehash: 7c1caf0ae27efce858328e5db88434253be61d50
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="activitytransfer"></a><span data-ttu-id="63c73-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="63c73-102">ActivityTransfer</span></span>
<span data-ttu-id="63c73-103">活動傳輸事件</span><span class="sxs-lookup"><span data-stu-id="63c73-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63c73-104">語法</span><span class="sxs-lookup"><span data-stu-id="63c73-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="63c73-105">方法</span><span class="sxs-lookup"><span data-stu-id="63c73-105">Methods</span></span>  
 <span data-ttu-id="63c73-106">ActivityTransfer 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="63c73-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="63c73-107">屬性</span><span class="sxs-lookup"><span data-stu-id="63c73-107">Properties</span></span>  
 <span data-ttu-id="63c73-108">ActivityTransfer 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="63c73-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="63c73-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="63c73-109">ActivityID</span></span>  
  
-   <span data-ttu-id="63c73-110">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="63c73-110">Data type: object</span></span>  
    <span data-ttu-id="63c73-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="63c73-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="63c73-112">活動識別碼</span><span class="sxs-lookup"><span data-stu-id="63c73-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="63c73-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="63c73-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="63c73-114">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="63c73-114">Data type: object</span></span>  
    <span data-ttu-id="63c73-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="63c73-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="63c73-116">相關活動識別碼</span><span class="sxs-lookup"><span data-stu-id="63c73-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63c73-117">需求</span><span class="sxs-lookup"><span data-stu-id="63c73-117">Requirements</span></span>  
  
|<span data-ttu-id="63c73-118">MOF</span><span class="sxs-lookup"><span data-stu-id="63c73-118">MOF</span></span>|<span data-ttu-id="63c73-119">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="63c73-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="63c73-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="63c73-120">Namespace</span></span>|<span data-ttu-id="63c73-121">於 root\ServiceModel 中定義。</span><span class="sxs-lookup"><span data-stu-id="63c73-121">Defined in root\ServiceModel.</span></span>|

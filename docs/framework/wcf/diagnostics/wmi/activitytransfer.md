---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 480670f19407321eb0928d07752936b2ece1f7e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484184"
---
# <a name="activitytransfer"></a><span data-ttu-id="122c9-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="122c9-102">ActivityTransfer</span></span>
<span data-ttu-id="122c9-103">活動傳輸事件</span><span class="sxs-lookup"><span data-stu-id="122c9-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="122c9-104">語法</span><span class="sxs-lookup"><span data-stu-id="122c9-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="122c9-105">方法</span><span class="sxs-lookup"><span data-stu-id="122c9-105">Methods</span></span>  
 <span data-ttu-id="122c9-106">ActivityTransfer 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="122c9-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="122c9-107">屬性</span><span class="sxs-lookup"><span data-stu-id="122c9-107">Properties</span></span>  
 <span data-ttu-id="122c9-108">ActivityTransfer 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="122c9-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="122c9-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="122c9-109">ActivityID</span></span>  
  
-   <span data-ttu-id="122c9-110">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="122c9-110">Data type: object</span></span>  
    <span data-ttu-id="122c9-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="122c9-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="122c9-112">活動識別碼</span><span class="sxs-lookup"><span data-stu-id="122c9-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="122c9-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="122c9-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="122c9-114">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="122c9-114">Data type: object</span></span>  
    <span data-ttu-id="122c9-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="122c9-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="122c9-116">相關活動識別碼</span><span class="sxs-lookup"><span data-stu-id="122c9-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="122c9-117">需求</span><span class="sxs-lookup"><span data-stu-id="122c9-117">Requirements</span></span>  
  
|<span data-ttu-id="122c9-118">MOF</span><span class="sxs-lookup"><span data-stu-id="122c9-118">MOF</span></span>|<span data-ttu-id="122c9-119">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="122c9-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="122c9-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="122c9-120">Namespace</span></span>|<span data-ttu-id="122c9-121">於 root\ServiceModel 中定義。</span><span class="sxs-lookup"><span data-stu-id="122c9-121">Defined in root\ServiceModel.</span></span>|

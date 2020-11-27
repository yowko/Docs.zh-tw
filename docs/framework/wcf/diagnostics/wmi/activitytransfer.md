---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: f1978881517fe5010ccc0f5192b21bd6688f063a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291111"
---
# <a name="activitytransfer"></a><span data-ttu-id="62c2f-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="62c2f-102">ActivityTransfer</span></span>

<span data-ttu-id="62c2f-103">活動傳輸事件</span><span class="sxs-lookup"><span data-stu-id="62c2f-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62c2f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="62c2f-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="62c2f-105">方法</span><span class="sxs-lookup"><span data-stu-id="62c2f-105">Methods</span></span>  

 <span data-ttu-id="62c2f-106">ActivityTransfer 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="62c2f-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="62c2f-107">屬性</span><span class="sxs-lookup"><span data-stu-id="62c2f-107">Properties</span></span>  

 <span data-ttu-id="62c2f-108">ActivityTransfer 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="62c2f-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="62c2f-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="62c2f-109">ActivityID</span></span>  
  
- <span data-ttu-id="62c2f-110">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="62c2f-110">Data type: object</span></span>  
    <span data-ttu-id="62c2f-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="62c2f-111">Access type: Read-only</span></span>  
  
- <span data-ttu-id="62c2f-112">活動識別碼</span><span class="sxs-lookup"><span data-stu-id="62c2f-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="62c2f-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="62c2f-113">RelatedActivityID</span></span>  
  
- <span data-ttu-id="62c2f-114">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="62c2f-114">Data type: object</span></span>  
    <span data-ttu-id="62c2f-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="62c2f-115">Access type: Read-only</span></span>  
  
- <span data-ttu-id="62c2f-116">相關活動識別碼</span><span class="sxs-lookup"><span data-stu-id="62c2f-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62c2f-117">規格需求</span><span class="sxs-lookup"><span data-stu-id="62c2f-117">Requirements</span></span>  
  
|<span data-ttu-id="62c2f-118">MOF</span><span class="sxs-lookup"><span data-stu-id="62c2f-118">MOF</span></span>|<span data-ttu-id="62c2f-119">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="62c2f-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="62c2f-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="62c2f-120">Namespace</span></span>|<span data-ttu-id="62c2f-121">於 root\ServiceModel 中定義。</span><span class="sxs-lookup"><span data-stu-id="62c2f-121">Defined in root\ServiceModel.</span></span>|

---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 6237d65d6964a4ebca34af895158c83239641593
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662815"
---
# <a name="activitytransfer"></a><span data-ttu-id="85385-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="85385-102">ActivityTransfer</span></span>
<span data-ttu-id="85385-103">活動傳輸事件</span><span class="sxs-lookup"><span data-stu-id="85385-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85385-104">語法</span><span class="sxs-lookup"><span data-stu-id="85385-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="85385-105">方法</span><span class="sxs-lookup"><span data-stu-id="85385-105">Methods</span></span>  
 <span data-ttu-id="85385-106">ActivityTransfer 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="85385-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="85385-107">屬性</span><span class="sxs-lookup"><span data-stu-id="85385-107">Properties</span></span>  
 <span data-ttu-id="85385-108">ActivityTransfer 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="85385-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="85385-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="85385-109">ActivityID</span></span>  
  
- <span data-ttu-id="85385-110">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="85385-110">Data type: object</span></span>  
    <span data-ttu-id="85385-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="85385-111">Access type: Read-only</span></span>  
  
- <span data-ttu-id="85385-112">活動識別碼</span><span class="sxs-lookup"><span data-stu-id="85385-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="85385-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="85385-113">RelatedActivityID</span></span>  
  
- <span data-ttu-id="85385-114">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="85385-114">Data type: object</span></span>  
    <span data-ttu-id="85385-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="85385-115">Access type: Read-only</span></span>  
  
- <span data-ttu-id="85385-116">相關活動識別碼</span><span class="sxs-lookup"><span data-stu-id="85385-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85385-117">需求</span><span class="sxs-lookup"><span data-stu-id="85385-117">Requirements</span></span>  
  
|<span data-ttu-id="85385-118">MOF</span><span class="sxs-lookup"><span data-stu-id="85385-118">MOF</span></span>|<span data-ttu-id="85385-119">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="85385-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="85385-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="85385-120">Namespace</span></span>|<span data-ttu-id="85385-121">於 root\ServiceModel 中定義。</span><span class="sxs-lookup"><span data-stu-id="85385-121">Defined in root\ServiceModel.</span></span>|

---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 936e870c1ec991e2e33acf8a08ccc93975989679
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964290"
---
# <a name="activitytransfer"></a><span data-ttu-id="ad471-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="ad471-102">ActivityTransfer</span></span>
<span data-ttu-id="ad471-103">活動傳輸事件</span><span class="sxs-lookup"><span data-stu-id="ad471-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad471-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad471-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ad471-105">方法</span><span class="sxs-lookup"><span data-stu-id="ad471-105">Methods</span></span>  
 <span data-ttu-id="ad471-106">ActivityTransfer 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="ad471-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ad471-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ad471-107">Properties</span></span>  
 <span data-ttu-id="ad471-108">ActivityTransfer 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="ad471-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="ad471-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="ad471-109">ActivityID</span></span>  
  
- <span data-ttu-id="ad471-110">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="ad471-110">Data type: object</span></span>  
    <span data-ttu-id="ad471-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ad471-111">Access type: Read-only</span></span>  
  
- <span data-ttu-id="ad471-112">活動識別碼</span><span class="sxs-lookup"><span data-stu-id="ad471-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="ad471-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="ad471-113">RelatedActivityID</span></span>  
  
- <span data-ttu-id="ad471-114">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="ad471-114">Data type: object</span></span>  
    <span data-ttu-id="ad471-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ad471-115">Access type: Read-only</span></span>  
  
- <span data-ttu-id="ad471-116">相關活動識別碼</span><span class="sxs-lookup"><span data-stu-id="ad471-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad471-117">需求</span><span class="sxs-lookup"><span data-stu-id="ad471-117">Requirements</span></span>  
  
|<span data-ttu-id="ad471-118">MOF</span><span class="sxs-lookup"><span data-stu-id="ad471-118">MOF</span></span>|<span data-ttu-id="ad471-119">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="ad471-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ad471-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="ad471-120">Namespace</span></span>|<span data-ttu-id="ad471-121">於 root\ServiceModel 中定義。</span><span class="sxs-lookup"><span data-stu-id="ad471-121">Defined in root\ServiceModel.</span></span>|

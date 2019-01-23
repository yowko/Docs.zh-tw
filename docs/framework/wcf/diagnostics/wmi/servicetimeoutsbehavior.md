---
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: b129483b60a62f04f522036c9d1fa54268f6f346
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566667"
---
# <a name="servicetimeoutsbehavior"></a><span data-ttu-id="3e3d5-102">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="3e3d5-102">ServiceTimeoutsBehavior</span></span>
<span data-ttu-id="3e3d5-103">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="3e3d5-103">ServiceTimeoutsBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e3d5-104">語法</span><span class="sxs-lookup"><span data-stu-id="3e3d5-104">Syntax</span></span>  
  
```csharp
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3e3d5-105">方法</span><span class="sxs-lookup"><span data-stu-id="3e3d5-105">Methods</span></span>  
 <span data-ttu-id="3e3d5-106">ServiceTimeoutsBehavior 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="3e3d5-106">The ServiceTimeoutsBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3e3d5-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3e3d5-107">Properties</span></span>  
 <span data-ttu-id="3e3d5-108">ServiceTimeoutsBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="3e3d5-108">The ServiceTimeoutsBehavior class has the following property:</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="3e3d5-109">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="3e3d5-109">TransactionTimeout</span></span>  
 <span data-ttu-id="3e3d5-110">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="3e3d5-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="3e3d5-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="3e3d5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e3d5-112">異動必須完成的期間。</span><span class="sxs-lookup"><span data-stu-id="3e3d5-112">The period within which a transaction must complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e3d5-113">需求</span><span class="sxs-lookup"><span data-stu-id="3e3d5-113">Requirements</span></span>  
  
|<span data-ttu-id="3e3d5-114">MOF</span><span class="sxs-lookup"><span data-stu-id="3e3d5-114">MOF</span></span>|<span data-ttu-id="3e3d5-115">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="3e3d5-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3e3d5-116">命名空間</span><span class="sxs-lookup"><span data-stu-id="3e3d5-116">Namespace</span></span>|<span data-ttu-id="3e3d5-117">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="3e3d5-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3e3d5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e3d5-118">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>

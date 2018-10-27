---
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: 1a5284915de739e95325234318842a4d1ab607be
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2018
ms.locfileid: "50135241"
---
# <a name="servicetimeoutsbehavior"></a><span data-ttu-id="f5f4d-102">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="f5f4d-102">ServiceTimeoutsBehavior</span></span>
<span data-ttu-id="f5f4d-103">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="f5f4d-103">ServiceTimeoutsBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5f4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5f4d-104">Syntax</span></span>  
  
```csharp
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f5f4d-105">方法</span><span class="sxs-lookup"><span data-stu-id="f5f4d-105">Methods</span></span>  
 <span data-ttu-id="f5f4d-106">ServiceTimeoutsBehavior 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="f5f4d-106">The ServiceTimeoutsBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f5f4d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f5f4d-107">Properties</span></span>  
 <span data-ttu-id="f5f4d-108">ServiceTimeoutsBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f5f4d-108">The ServiceTimeoutsBehavior class has the following property:</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="f5f4d-109">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="f5f4d-109">TransactionTimeout</span></span>  
 <span data-ttu-id="f5f4d-110">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="f5f4d-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="f5f4d-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f5f4d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f5f4d-112">交易必須完成的期間。</span><span class="sxs-lookup"><span data-stu-id="f5f4d-112">The period within which a transaction must complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5f4d-113">需求</span><span class="sxs-lookup"><span data-stu-id="f5f4d-113">Requirements</span></span>  
  
|<span data-ttu-id="f5f4d-114">MOF</span><span class="sxs-lookup"><span data-stu-id="f5f4d-114">MOF</span></span>|<span data-ttu-id="f5f4d-115">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="f5f4d-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f5f4d-116">命名空間</span><span class="sxs-lookup"><span data-stu-id="f5f4d-116">Namespace</span></span>|<span data-ttu-id="f5f4d-117">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="f5f4d-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5f4d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5f4d-118">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>

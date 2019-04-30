---
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: 58e872f2b15776d65bccdcc47c353ce566cd9d2f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956724"
---
# <a name="servicetimeoutsbehavior"></a><span data-ttu-id="03f0d-102">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="03f0d-102">ServiceTimeoutsBehavior</span></span>
<span data-ttu-id="03f0d-103">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="03f0d-103">ServiceTimeoutsBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03f0d-104">語法</span><span class="sxs-lookup"><span data-stu-id="03f0d-104">Syntax</span></span>  
  
```csharp
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="03f0d-105">方法</span><span class="sxs-lookup"><span data-stu-id="03f0d-105">Methods</span></span>  
 <span data-ttu-id="03f0d-106">ServiceTimeoutsBehavior 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="03f0d-106">The ServiceTimeoutsBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="03f0d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="03f0d-107">Properties</span></span>  
 <span data-ttu-id="03f0d-108">ServiceTimeoutsBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="03f0d-108">The ServiceTimeoutsBehavior class has the following property:</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="03f0d-109">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="03f0d-109">TransactionTimeout</span></span>  
 <span data-ttu-id="03f0d-110">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="03f0d-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="03f0d-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="03f0d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03f0d-112">異動必須完成的期間。</span><span class="sxs-lookup"><span data-stu-id="03f0d-112">The period within which a transaction must complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03f0d-113">需求</span><span class="sxs-lookup"><span data-stu-id="03f0d-113">Requirements</span></span>  
  
|<span data-ttu-id="03f0d-114">MOF</span><span class="sxs-lookup"><span data-stu-id="03f0d-114">MOF</span></span>|<span data-ttu-id="03f0d-115">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="03f0d-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="03f0d-116">命名空間</span><span class="sxs-lookup"><span data-stu-id="03f0d-116">Namespace</span></span>|<span data-ttu-id="03f0d-117">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="03f0d-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03f0d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03f0d-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>

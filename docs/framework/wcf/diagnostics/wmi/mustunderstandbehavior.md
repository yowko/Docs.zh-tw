---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 0f3efc446104a1afff507f6e7d2cd8c01c4ed417
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452595"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="941bd-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="941bd-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="941bd-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="941bd-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="941bd-104">語法</span><span class="sxs-lookup"><span data-stu-id="941bd-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="941bd-105">方法</span><span class="sxs-lookup"><span data-stu-id="941bd-105">Methods</span></span>  
 <span data-ttu-id="941bd-106">MustUnderstandBehavior 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="941bd-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="941bd-107">屬性</span><span class="sxs-lookup"><span data-stu-id="941bd-107">Properties</span></span>  
 <span data-ttu-id="941bd-108">MustUnderstandBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="941bd-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="941bd-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="941bd-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="941bd-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="941bd-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="941bd-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="941bd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="941bd-112">當 `true``MustUnderstand`時，所有具有  屬性且未處理的 SOAP 標頭，會導致該行為擲出例外狀況。</span><span class="sxs-lookup"><span data-stu-id="941bd-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="941bd-113">需求</span><span class="sxs-lookup"><span data-stu-id="941bd-113">Requirements</span></span>  
  
|<span data-ttu-id="941bd-114">MOF</span><span class="sxs-lookup"><span data-stu-id="941bd-114">MOF</span></span>|<span data-ttu-id="941bd-115">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="941bd-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="941bd-116">命名空間</span><span class="sxs-lookup"><span data-stu-id="941bd-116">Namespace</span></span>|<span data-ttu-id="941bd-117">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="941bd-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="941bd-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="941bd-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>

---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 0f3efc446104a1afff507f6e7d2cd8c01c4ed417
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49371792"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="111d5-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="111d5-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="111d5-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="111d5-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="111d5-104">語法</span><span class="sxs-lookup"><span data-stu-id="111d5-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="111d5-105">方法</span><span class="sxs-lookup"><span data-stu-id="111d5-105">Methods</span></span>  
 <span data-ttu-id="111d5-106">MustUnderstandBehavior 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="111d5-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="111d5-107">屬性</span><span class="sxs-lookup"><span data-stu-id="111d5-107">Properties</span></span>  
 <span data-ttu-id="111d5-108">MustUnderstandBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="111d5-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="111d5-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="111d5-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="111d5-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="111d5-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="111d5-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="111d5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="111d5-112">當 `true``MustUnderstand`時，所有具有  屬性且未處理的 SOAP 標頭，會導致該行為擲出例外狀況。</span><span class="sxs-lookup"><span data-stu-id="111d5-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="111d5-113">需求</span><span class="sxs-lookup"><span data-stu-id="111d5-113">Requirements</span></span>  
  
|<span data-ttu-id="111d5-114">MOF</span><span class="sxs-lookup"><span data-stu-id="111d5-114">MOF</span></span>|<span data-ttu-id="111d5-115">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="111d5-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="111d5-116">命名空間</span><span class="sxs-lookup"><span data-stu-id="111d5-116">Namespace</span></span>|<span data-ttu-id="111d5-117">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="111d5-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="111d5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="111d5-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>

---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 334bab97a04ed464dce6944692b04a9ed1295296
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613816"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="fff9e-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="fff9e-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="fff9e-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="fff9e-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fff9e-104">語法</span><span class="sxs-lookup"><span data-stu-id="fff9e-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fff9e-105">方法</span><span class="sxs-lookup"><span data-stu-id="fff9e-105">Methods</span></span>  
 <span data-ttu-id="fff9e-106">MustUnderstandBehavior 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="fff9e-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fff9e-107">屬性</span><span class="sxs-lookup"><span data-stu-id="fff9e-107">Properties</span></span>  
 <span data-ttu-id="fff9e-108">MustUnderstandBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="fff9e-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="fff9e-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="fff9e-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="fff9e-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="fff9e-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="fff9e-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fff9e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fff9e-112">當 `true``MustUnderstand`時，所有具有  屬性且未處理的 SOAP 標頭，會導致該行為擲出例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fff9e-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fff9e-113">需求</span><span class="sxs-lookup"><span data-stu-id="fff9e-113">Requirements</span></span>  
  
|<span data-ttu-id="fff9e-114">MOF</span><span class="sxs-lookup"><span data-stu-id="fff9e-114">MOF</span></span>|<span data-ttu-id="fff9e-115">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="fff9e-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fff9e-116">命名空間</span><span class="sxs-lookup"><span data-stu-id="fff9e-116">Namespace</span></span>|<span data-ttu-id="fff9e-117">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="fff9e-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fff9e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fff9e-118">See also</span></span>
- <xref:System.ServiceModel.Description.MustUnderstandBehavior>

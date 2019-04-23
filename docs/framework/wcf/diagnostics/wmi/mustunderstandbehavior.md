---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 7e6a96c217b038e870b4e865315766afa3b3c757
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975338"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="f3369-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="f3369-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="f3369-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="f3369-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3369-104">語法</span><span class="sxs-lookup"><span data-stu-id="f3369-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f3369-105">方法</span><span class="sxs-lookup"><span data-stu-id="f3369-105">Methods</span></span>  
 <span data-ttu-id="f3369-106">MustUnderstandBehavior 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="f3369-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f3369-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f3369-107">Properties</span></span>  
 <span data-ttu-id="f3369-108">MustUnderstandBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f3369-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="f3369-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="f3369-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="f3369-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="f3369-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="f3369-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f3369-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f3369-112">當 `true``MustUnderstand`時，所有具有  屬性且未處理的 SOAP 標頭，會導致該行為擲出例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f3369-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3369-113">需求</span><span class="sxs-lookup"><span data-stu-id="f3369-113">Requirements</span></span>  
  
|<span data-ttu-id="f3369-114">MOF</span><span class="sxs-lookup"><span data-stu-id="f3369-114">MOF</span></span>|<span data-ttu-id="f3369-115">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="f3369-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f3369-116">命名空間</span><span class="sxs-lookup"><span data-stu-id="f3369-116">Namespace</span></span>|<span data-ttu-id="f3369-117">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="f3369-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3369-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3369-118">See also</span></span>

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>

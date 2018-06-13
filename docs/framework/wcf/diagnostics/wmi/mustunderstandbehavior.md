---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 14150a992130e9ed4734c950d4ed92f1bbd3206c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485553"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="c6bd6-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="c6bd6-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="c6bd6-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="c6bd6-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6bd6-104">語法</span><span class="sxs-lookup"><span data-stu-id="c6bd6-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c6bd6-105">方法</span><span class="sxs-lookup"><span data-stu-id="c6bd6-105">Methods</span></span>  
 <span data-ttu-id="c6bd6-106">MustUnderstandBehavior 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="c6bd6-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c6bd6-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c6bd6-107">Properties</span></span>  
 <span data-ttu-id="c6bd6-108">MustUnderstandBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="c6bd6-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="c6bd6-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="c6bd6-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="c6bd6-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="c6bd6-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="c6bd6-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c6bd6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c6bd6-112">當 `true``MustUnderstand`時，所有具有  屬性且未處理的 SOAP 標頭，會導致該行為擲出例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c6bd6-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6bd6-113">需求</span><span class="sxs-lookup"><span data-stu-id="c6bd6-113">Requirements</span></span>  
  
|<span data-ttu-id="c6bd6-114">MOF</span><span class="sxs-lookup"><span data-stu-id="c6bd6-114">MOF</span></span>|<span data-ttu-id="c6bd6-115">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="c6bd6-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c6bd6-116">命名空間</span><span class="sxs-lookup"><span data-stu-id="c6bd6-116">Namespace</span></span>|<span data-ttu-id="c6bd6-117">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="c6bd6-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6bd6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6bd6-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>

---
title: MustUnderstandBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dca98f1d8d5f868285ecf11c01122f795ee6cfd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="e0035-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="e0035-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="e0035-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="e0035-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0035-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0035-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e0035-105">方法</span><span class="sxs-lookup"><span data-stu-id="e0035-105">Methods</span></span>  
 <span data-ttu-id="e0035-106">MustUnderstandBehavior 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="e0035-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e0035-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e0035-107">Properties</span></span>  
 <span data-ttu-id="e0035-108">MustUnderstandBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e0035-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="e0035-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="e0035-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="e0035-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="e0035-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="e0035-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="e0035-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0035-112">當 `true``MustUnderstand`時，所有具有  屬性且未處理的 SOAP 標頭，會導致該行為擲出例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e0035-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0035-113">需求</span><span class="sxs-lookup"><span data-stu-id="e0035-113">Requirements</span></span>  
  
|<span data-ttu-id="e0035-114">MOF</span><span class="sxs-lookup"><span data-stu-id="e0035-114">MOF</span></span>|<span data-ttu-id="e0035-115">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="e0035-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e0035-116">命名空間</span><span class="sxs-lookup"><span data-stu-id="e0035-116">Namespace</span></span>|<span data-ttu-id="e0035-117">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="e0035-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0035-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0035-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>

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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 40075acb2a098c98b4cd0ab35f213981c09f8486
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="d43c4-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="d43c4-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="d43c4-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="d43c4-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d43c4-104">語法</span><span class="sxs-lookup"><span data-stu-id="d43c4-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d43c4-105">方法</span><span class="sxs-lookup"><span data-stu-id="d43c4-105">Methods</span></span>  
 <span data-ttu-id="d43c4-106">MustUnderstandBehavior 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="d43c4-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d43c4-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d43c4-107">Properties</span></span>  
 <span data-ttu-id="d43c4-108">MustUnderstandBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d43c4-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="d43c4-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="d43c4-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="d43c4-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="d43c4-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="d43c4-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="d43c4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d43c4-112">當 `true``MustUnderstand`時，所有具有  屬性且未處理的 SOAP 標頭，會導致該行為擲出例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d43c4-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d43c4-113">需求</span><span class="sxs-lookup"><span data-stu-id="d43c4-113">Requirements</span></span>  
  
|<span data-ttu-id="d43c4-114">MOF</span><span class="sxs-lookup"><span data-stu-id="d43c4-114">MOF</span></span>|<span data-ttu-id="d43c4-115">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="d43c4-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d43c4-116">命名空間</span><span class="sxs-lookup"><span data-stu-id="d43c4-116">Namespace</span></span>|<span data-ttu-id="d43c4-117">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="d43c4-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d43c4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d43c4-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>

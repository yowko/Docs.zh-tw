---
title: "EnumCustomAttributes 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d616babb47ac0282ef56d119ab448a94fd24c7c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="3ee0c-102">EnumCustomAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="3ee0c-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="3ee0c-103">擷取組件層級自訂的屬性。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ee0c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3ee0c-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ee0c-105">參數</span><span class="sxs-lookup"><span data-stu-id="3ee0c-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="3ee0c-106">列舉值的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="3ee0c-107">要列舉的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="3ee0c-108">使用`mdTokenNill`所有屬性。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="3ee0c-109">接收權杖的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3ee0c-110">指定的大小`rCustomValues`陣列。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="3ee0c-111">（選擇性） 接收語彙基元值的計數。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ee0c-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="3ee0c-112">Return Value</span></span>  
 <span data-ttu-id="3ee0c-113">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ee0c-114">需求</span><span class="sxs-lookup"><span data-stu-id="3ee0c-114">Requirements</span></span>  
 <span data-ttu-id="3ee0c-115">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="3ee0c-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee0c-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="3ee0c-116">See Also</span></span>  
 [<span data-ttu-id="3ee0c-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="3ee0c-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="3ee0c-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="3ee0c-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="3ee0c-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="3ee0c-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

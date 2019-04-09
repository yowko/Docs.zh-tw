---
title: EnumCustomAttributes 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b419962982fc80591ed565cceb28afb88a39495e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199137"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="6dd85-102">EnumCustomAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="6dd85-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="6dd85-103">擷取組件層級自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="6dd85-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dd85-104">語法</span><span class="sxs-lookup"><span data-stu-id="6dd85-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6dd85-105">參數</span><span class="sxs-lookup"><span data-stu-id="6dd85-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="6dd85-106">列舉值的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="6dd85-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="6dd85-107">要列舉的屬性型別。</span><span class="sxs-lookup"><span data-stu-id="6dd85-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="6dd85-108">使用`mdTokenNill`的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="6dd85-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="6dd85-109">接收權杖的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="6dd85-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6dd85-110">指定的大小`rCustomValues`陣列。</span><span class="sxs-lookup"><span data-stu-id="6dd85-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="6dd85-111">選擇性地接收的權杖值的計數。</span><span class="sxs-lookup"><span data-stu-id="6dd85-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6dd85-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="6dd85-112">Return Value</span></span>  
 <span data-ttu-id="6dd85-113">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="6dd85-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dd85-114">需求</span><span class="sxs-lookup"><span data-stu-id="6dd85-114">Requirements</span></span>  
 <span data-ttu-id="6dd85-115">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="6dd85-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dd85-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dd85-116">See also</span></span>

- [<span data-ttu-id="6dd85-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="6dd85-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="6dd85-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="6dd85-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="6dd85-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="6dd85-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

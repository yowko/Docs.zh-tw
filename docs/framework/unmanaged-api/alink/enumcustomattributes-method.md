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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789970"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="523ef-102">EnumCustomAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="523ef-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="523ef-103">擷取組件層級自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="523ef-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="523ef-104">語法</span><span class="sxs-lookup"><span data-stu-id="523ef-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="523ef-105">參數</span><span class="sxs-lookup"><span data-stu-id="523ef-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="523ef-106">列舉值的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="523ef-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="523ef-107">要列舉的屬性型別。</span><span class="sxs-lookup"><span data-stu-id="523ef-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="523ef-108">使用`mdTokenNill`的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="523ef-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="523ef-109">接收權杖的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="523ef-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="523ef-110">指定的大小`rCustomValues`陣列。</span><span class="sxs-lookup"><span data-stu-id="523ef-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="523ef-111">選擇性地接收的權杖值的計數。</span><span class="sxs-lookup"><span data-stu-id="523ef-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="523ef-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="523ef-112">Return Value</span></span>  
 <span data-ttu-id="523ef-113">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="523ef-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="523ef-114">需求</span><span class="sxs-lookup"><span data-stu-id="523ef-114">Requirements</span></span>  
 <span data-ttu-id="523ef-115">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="523ef-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="523ef-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="523ef-116">See also</span></span>

- [<span data-ttu-id="523ef-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="523ef-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="523ef-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="523ef-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="523ef-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="523ef-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

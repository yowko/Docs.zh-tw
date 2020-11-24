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
ms.openlocfilehash: 445c833d10631341ef7ad579eaff8ddd96be3428
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684846"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="21611-102">EnumCustomAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="21611-102">EnumCustomAttributes Method</span></span>

<span data-ttu-id="21611-103">捕獲元件層級的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="21611-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21611-104">語法</span><span class="sxs-lookup"><span data-stu-id="21611-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="21611-105">參數</span><span class="sxs-lookup"><span data-stu-id="21611-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="21611-106">列舉值的控制碼。</span><span class="sxs-lookup"><span data-stu-id="21611-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="21611-107">要列舉的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="21611-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="21611-108">用於 `mdTokenNill` 所有屬性。</span><span class="sxs-lookup"><span data-stu-id="21611-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="21611-109">接收自訂屬性標記。</span><span class="sxs-lookup"><span data-stu-id="21611-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="21611-110">指定陣列的大小 `rCustomValues` 。</span><span class="sxs-lookup"><span data-stu-id="21611-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="21611-111">選擇性地接收權杖值的計數。</span><span class="sxs-lookup"><span data-stu-id="21611-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21611-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="21611-112">Return Value</span></span>  

 <span data-ttu-id="21611-113">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="21611-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21611-114">需求</span><span class="sxs-lookup"><span data-stu-id="21611-114">Requirements</span></span>  

 <span data-ttu-id="21611-115">需要 alink。h</span><span class="sxs-lookup"><span data-stu-id="21611-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21611-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21611-116">See also</span></span>

- [<span data-ttu-id="21611-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="21611-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="21611-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="21611-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="21611-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="21611-119">ALink API</span></span>](index.md)

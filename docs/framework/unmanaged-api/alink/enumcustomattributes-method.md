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
ms.openlocfilehash: 5d8827f46a12bd090fa27e71072d833607d34677
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777358"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="8cac7-102">EnumCustomAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="8cac7-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="8cac7-103">抓取元件層級的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="8cac7-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cac7-104">語法</span><span class="sxs-lookup"><span data-stu-id="8cac7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cac7-105">參數</span><span class="sxs-lookup"><span data-stu-id="8cac7-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="8cac7-106">列舉值的控制碼。</span><span class="sxs-lookup"><span data-stu-id="8cac7-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="8cac7-107">要列舉的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="8cac7-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="8cac7-108">`mdTokenNill`用於所有屬性。</span><span class="sxs-lookup"><span data-stu-id="8cac7-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="8cac7-109">接收自訂屬性標記。</span><span class="sxs-lookup"><span data-stu-id="8cac7-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8cac7-110">指定陣列的`rCustomValues`大小。</span><span class="sxs-lookup"><span data-stu-id="8cac7-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="8cac7-111">選擇性地接收權杖值的計數。</span><span class="sxs-lookup"><span data-stu-id="8cac7-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8cac7-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="8cac7-112">Return Value</span></span>  
 <span data-ttu-id="8cac7-113">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="8cac7-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cac7-114">需求</span><span class="sxs-lookup"><span data-stu-id="8cac7-114">Requirements</span></span>  
 <span data-ttu-id="8cac7-115">需要 alink. h</span><span class="sxs-lookup"><span data-stu-id="8cac7-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cac7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cac7-116">See also</span></span>

- [<span data-ttu-id="8cac7-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="8cac7-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8cac7-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="8cac7-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8cac7-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="8cac7-119">ALink API</span></span>](index.md)

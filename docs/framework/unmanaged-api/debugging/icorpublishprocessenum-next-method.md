---
title: ICorPublishProcessEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type:
- apiref
ms.openlocfilehash: 084af87acd73ef65739ba69ef2bd66d10d7c27c2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790519"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="9b8c8-102">ICorPublishProcessEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="9b8c8-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="9b8c8-103">從目前的資料指標位置開始，取得集合中指定的進程數目。</span><span class="sxs-lookup"><span data-stu-id="9b8c8-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b8c8-104">語法</span><span class="sxs-lookup"><span data-stu-id="9b8c8-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b8c8-105">參數</span><span class="sxs-lookup"><span data-stu-id="9b8c8-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9b8c8-106">在要抓取的進程數目。</span><span class="sxs-lookup"><span data-stu-id="9b8c8-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="9b8c8-107">脫銷已抓取[ICorPublishProcess](icorpublishprocess-interface.md)物件之陣列的指標，每個物件都代表一個進程。</span><span class="sxs-lookup"><span data-stu-id="9b8c8-107">[out] A pointer to the array of retrieved [ICorPublishProcess](icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9b8c8-108">脫銷實際傳回之進程數目的指標。</span><span class="sxs-lookup"><span data-stu-id="9b8c8-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="9b8c8-109">如果 `celt` 為 null，這個值可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="9b8c8-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b8c8-110">需求</span><span class="sxs-lookup"><span data-stu-id="9b8c8-110">Requirements</span></span>  
 <span data-ttu-id="9b8c8-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b8c8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b8c8-112">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="9b8c8-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9b8c8-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b8c8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b8c8-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b8c8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b8c8-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="9b8c8-115">See also</span></span>

- [<span data-ttu-id="9b8c8-116">ICorPublishProcessEnum 介面</span><span class="sxs-lookup"><span data-stu-id="9b8c8-116">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)

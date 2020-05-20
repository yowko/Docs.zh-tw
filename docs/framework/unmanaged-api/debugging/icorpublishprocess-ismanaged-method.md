---
title: ICorPublishProcess::IsManaged 方法
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: 3eec84624866b2be7068d7875cd650828c283fd2
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421094"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="ce855-102">ICorPublishProcess::IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="ce855-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="ce855-103">取得值，指出此[ICorPublishProcess](icorpublishprocess-interface.md)所參考的進程是否已知具有 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ce855-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce855-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce855-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce855-105">參數</span><span class="sxs-lookup"><span data-stu-id="ce855-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="ce855-106">脫銷布林值的指標，指出進程是否有 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ce855-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="ce855-107">`true`如果進程具有 managed 程式碼，則值為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ce855-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce855-108">備註</span><span class="sxs-lookup"><span data-stu-id="ce855-108">Remarks</span></span>  
 <span data-ttu-id="ce855-109">由於目前的版本 `ICorPublishProcess` 只允許存取具有 managed 程式碼的進程，因此 `IsManaged` 一律會傳回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="ce855-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce855-110">需求</span><span class="sxs-lookup"><span data-stu-id="ce855-110">Requirements</span></span>  
 <span data-ttu-id="ce855-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce855-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce855-112">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="ce855-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ce855-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce855-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce855-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce855-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce855-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce855-115">See also</span></span>

- [<span data-ttu-id="ce855-116">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="ce855-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)

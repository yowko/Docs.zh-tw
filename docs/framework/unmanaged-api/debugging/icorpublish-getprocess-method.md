---
title: ICorPublish::GetProcess 方法
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
ms.openlocfilehash: 2cd2238ac67713564922be440ce64a2ebc4bbf44
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396340"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="62299-102">ICorPublish::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="62299-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="62299-103">取得[ICorPublishProcess](icorpublishprocess-interface.md)實例，表示具有指定之識別碼的進程。</span><span class="sxs-lookup"><span data-stu-id="62299-103">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62299-104">語法</span><span class="sxs-lookup"><span data-stu-id="62299-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62299-105">參數</span><span class="sxs-lookup"><span data-stu-id="62299-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="62299-106">在進程的識別碼。</span><span class="sxs-lookup"><span data-stu-id="62299-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="62299-107">脫銷代表進程之實例位址的指標 `ICorPublishProcess` 。</span><span class="sxs-lookup"><span data-stu-id="62299-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62299-108">備註</span><span class="sxs-lookup"><span data-stu-id="62299-108">Remarks</span></span>  
 <span data-ttu-id="62299-109">`GetProcess`如果進程不存在，或不是目前使用者可以進行的 managed 進程，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="62299-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62299-110">需求</span><span class="sxs-lookup"><span data-stu-id="62299-110">Requirements</span></span>  
 <span data-ttu-id="62299-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62299-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62299-112">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="62299-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="62299-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62299-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62299-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62299-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62299-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="62299-115">See also</span></span>

- [<span data-ttu-id="62299-116">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="62299-116">ICorPublish Interface</span></span>](icorpublish-interface.md)

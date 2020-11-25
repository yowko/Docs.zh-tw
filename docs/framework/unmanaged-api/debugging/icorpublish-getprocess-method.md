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
ms.openlocfilehash: a45f613b7547e2e80abdbd8ac85cb0b2b6a499e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716885"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="d36da-102">ICorPublish::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="d36da-102">ICorPublish::GetProcess Method</span></span>

<span data-ttu-id="d36da-103">取得 [ICorPublishProcess](icorpublishprocess-interface.md) 實例，表示具有指定之識別碼的進程。</span><span class="sxs-lookup"><span data-stu-id="d36da-103">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d36da-104">語法</span><span class="sxs-lookup"><span data-stu-id="d36da-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d36da-105">參數</span><span class="sxs-lookup"><span data-stu-id="d36da-105">Parameters</span></span>  

 `pid`  
 <span data-ttu-id="d36da-106">在進程的識別碼。</span><span class="sxs-lookup"><span data-stu-id="d36da-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="d36da-107">擴展表示進程之實例的位址指標 `ICorPublishProcess` 。</span><span class="sxs-lookup"><span data-stu-id="d36da-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d36da-108">備註</span><span class="sxs-lookup"><span data-stu-id="d36da-108">Remarks</span></span>  

 <span data-ttu-id="d36da-109">`GetProcess` 如果進程不存在，或不是可由目前使用者進行偵錯工具的 managed 進程，就會失敗。</span><span class="sxs-lookup"><span data-stu-id="d36da-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d36da-110">需求</span><span class="sxs-lookup"><span data-stu-id="d36da-110">Requirements</span></span>  

 <span data-ttu-id="d36da-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d36da-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d36da-112">**標頭：** CorPub .idl、CorPub。h</span><span class="sxs-lookup"><span data-stu-id="d36da-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d36da-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d36da-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d36da-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d36da-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d36da-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d36da-115">See also</span></span>

- [<span data-ttu-id="d36da-116">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="d36da-116">ICorPublish Interface</span></span>](icorpublish-interface.md)

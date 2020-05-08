---
title: ICorDebugAppDomainEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type:
- apiref
ms.openlocfilehash: 17bf4c92b1e1347a8fe790c8df5937de0f95df4d
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895076"
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="16020-102">ICorDebugAppDomainEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="16020-102">ICorDebugAppDomainEnum::Next Method</span></span>
<span data-ttu-id="16020-103">從目前的資料指標位置開始，取得集合中指定的應用程式域數目。</span><span class="sxs-lookup"><span data-stu-id="16020-103">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16020-104">語法</span><span class="sxs-lookup"><span data-stu-id="16020-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16020-105">參數</span><span class="sxs-lookup"><span data-stu-id="16020-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="16020-106">在要抓取的應用程式域數目。</span><span class="sxs-lookup"><span data-stu-id="16020-106">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="16020-107">脫銷指標陣列，其中每一個都會指向代表應用程式域的 ICorDebugAppDomain 物件。</span><span class="sxs-lookup"><span data-stu-id="16020-107">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="16020-108">脫銷實際傳回的應用程式網域數目的指標。</span><span class="sxs-lookup"><span data-stu-id="16020-108">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="16020-109">如果`celt`是一個，這個值可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="16020-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16020-110">需求</span><span class="sxs-lookup"><span data-stu-id="16020-110">Requirements</span></span>  
 <span data-ttu-id="16020-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="16020-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16020-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16020-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16020-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16020-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16020-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16020-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

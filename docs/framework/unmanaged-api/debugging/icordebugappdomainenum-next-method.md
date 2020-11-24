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
ms.openlocfilehash: b315f38dc306727e33b52b84d17951a91ccdc39f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684469"
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="6f1ac-102">ICorDebugAppDomainEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="6f1ac-102">ICorDebugAppDomainEnum::Next Method</span></span>

<span data-ttu-id="6f1ac-103">從目前的資料指標位置開始，取得集合中指定的應用程式域數目。</span><span class="sxs-lookup"><span data-stu-id="6f1ac-103">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f1ac-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f1ac-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f1ac-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f1ac-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="6f1ac-106">在要取出的應用程式域數目。</span><span class="sxs-lookup"><span data-stu-id="6f1ac-106">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="6f1ac-107">擴展指標的陣列，每個指標都會指向代表應用程式域的 ICorDebugAppDomain 物件。</span><span class="sxs-lookup"><span data-stu-id="6f1ac-107">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6f1ac-108">擴展實際傳回的應用程式域數目指標。</span><span class="sxs-lookup"><span data-stu-id="6f1ac-108">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="6f1ac-109">如果是1，則這個值可能是 null `celt` 。</span><span class="sxs-lookup"><span data-stu-id="6f1ac-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f1ac-110">需求</span><span class="sxs-lookup"><span data-stu-id="6f1ac-110">Requirements</span></span>  

 <span data-ttu-id="6f1ac-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f1ac-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f1ac-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f1ac-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f1ac-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f1ac-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f1ac-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f1ac-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

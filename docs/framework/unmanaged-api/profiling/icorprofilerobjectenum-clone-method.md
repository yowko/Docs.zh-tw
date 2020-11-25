---
title: ICorProfilerObjectEnum::Clone 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
ms.openlocfilehash: df1d5881bccdb357b16c7f02cd090388e0f66273
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722800"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="f0ab6-102">ICorProfilerObjectEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="f0ab6-102">ICorProfilerObjectEnum::Clone Method</span></span>

<span data-ttu-id="f0ab6-103">取得這個 [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) 介面複本的介面指標。</span><span class="sxs-lookup"><span data-stu-id="f0ab6-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0ab6-104">語法</span><span class="sxs-lookup"><span data-stu-id="f0ab6-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0ab6-105">參數</span><span class="sxs-lookup"><span data-stu-id="f0ab6-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="f0ab6-106">擴展指向介面指標的指標，該指標會指向這個介面的複本 `ICorProfilerObjectEnum` 。</span><span class="sxs-lookup"><span data-stu-id="f0ab6-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="f0ab6-107">複製會彼此獨立地維護自己的列舉狀態。</span><span class="sxs-lookup"><span data-stu-id="f0ab6-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="f0ab6-108">不過，複本的初始游標位置將與此列舉值的目前資料指標位置相同。</span><span class="sxs-lookup"><span data-stu-id="f0ab6-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0ab6-109">需求</span><span class="sxs-lookup"><span data-stu-id="f0ab6-109">Requirements</span></span>  

 <span data-ttu-id="f0ab6-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f0ab6-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0ab6-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f0ab6-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f0ab6-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0ab6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0ab6-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0ab6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ab6-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0ab6-114">See also</span></span>

- [<span data-ttu-id="f0ab6-115">ICorProfilerObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="f0ab6-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)

---
title: ICorDebugLoadedModule::GetSize 方法
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 6a1c8c94b3c45ac995501b84bb4a69d73e7db25b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209847"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="f1ca8-102">ICorDebugLoadedModule::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="f1ca8-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="f1ca8-103">取得載入模組的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="f1ca8-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1ca8-104">語法</span><span class="sxs-lookup"><span data-stu-id="f1ca8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1ca8-105">參數</span><span class="sxs-lookup"><span data-stu-id="f1ca8-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="f1ca8-106">[out] 載入模組中之位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="f1ca8-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1ca8-107">備註</span><span class="sxs-lookup"><span data-stu-id="f1ca8-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1ca8-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="f1ca8-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1ca8-109">需求</span><span class="sxs-lookup"><span data-stu-id="f1ca8-109">Requirements</span></span>  
 <span data-ttu-id="f1ca8-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ca8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1ca8-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1ca8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1ca8-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1ca8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1ca8-113">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1ca8-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1ca8-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="f1ca8-114">See also</span></span>

- [<span data-ttu-id="f1ca8-115">ICorDebugLoadedModule 介面</span><span class="sxs-lookup"><span data-stu-id="f1ca8-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="f1ca8-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f1ca8-116">Debugging Interfaces</span></span>](debugging-interfaces.md)

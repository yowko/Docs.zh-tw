---
title: ICorDebugLoadedModule::GetSize 方法
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 2ed19cb4a190f2af7581a827e8bd11b748b3d4a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721318"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="32794-102">ICorDebugLoadedModule::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="32794-102">ICorDebugLoadedModule::GetSize Method</span></span>

<span data-ttu-id="32794-103">取得載入模組的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="32794-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32794-104">語法</span><span class="sxs-lookup"><span data-stu-id="32794-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32794-105">參數</span><span class="sxs-lookup"><span data-stu-id="32794-105">Parameters</span></span>  

 `pcBytes`  
 <span data-ttu-id="32794-106">[out] 載入模組中之位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="32794-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32794-107">備註</span><span class="sxs-lookup"><span data-stu-id="32794-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32794-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="32794-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32794-109">需求</span><span class="sxs-lookup"><span data-stu-id="32794-109">Requirements</span></span>  

 <span data-ttu-id="32794-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32794-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32794-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32794-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32794-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32794-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32794-113">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32794-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32794-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32794-114">See also</span></span>

- [<span data-ttu-id="32794-115">ICorDebugLoadedModule 介面</span><span class="sxs-lookup"><span data-stu-id="32794-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="32794-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="32794-116">Debugging Interfaces</span></span>](debugging-interfaces.md)

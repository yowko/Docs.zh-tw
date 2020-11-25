---
title: ICorDebugLoadedModule::GetBaseAddress 方法
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: 29153da86812583a0ea789da0c0816f08e0a6b43
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698074"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="95af3-102">ICorDebugLoadedModule::GetBaseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="95af3-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>

<span data-ttu-id="95af3-103">取得載入模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="95af3-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95af3-104">語法</span><span class="sxs-lookup"><span data-stu-id="95af3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95af3-105">參數</span><span class="sxs-lookup"><span data-stu-id="95af3-105">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="95af3-106">[out] 載入模組的基底位址指標。</span><span class="sxs-lookup"><span data-stu-id="95af3-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95af3-107">備註</span><span class="sxs-lookup"><span data-stu-id="95af3-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95af3-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="95af3-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95af3-109">需求</span><span class="sxs-lookup"><span data-stu-id="95af3-109">Requirements</span></span>  

 <span data-ttu-id="95af3-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95af3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95af3-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95af3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95af3-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95af3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95af3-113">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95af3-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95af3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95af3-114">See also</span></span>

- [<span data-ttu-id="95af3-115">ICorDebugLoadedModule 介面</span><span class="sxs-lookup"><span data-stu-id="95af3-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="95af3-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="95af3-116">Debugging Interfaces</span></span>](debugging-interfaces.md)

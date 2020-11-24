---
title: ICorDebugAssembly3::GetContainerAssembly 方法
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 51e68e73983425cdd7d648b6856809fcba590f70
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688545"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="cf903-102">ICorDebugAssembly3::GetContainerAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="cf903-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>

<span data-ttu-id="cf903-103">傳回這個 `ICorDebugAssembly3` 物件的容器組件。</span><span class="sxs-lookup"><span data-stu-id="cf903-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf903-104">語法</span><span class="sxs-lookup"><span data-stu-id="cf903-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf903-105">參數</span><span class="sxs-lookup"><span data-stu-id="cf903-105">Parameters</span></span>  

 `ppAssembly`  
 <span data-ttu-id="cf903-106">代表容器元件之 ICorDebugAssembly 物件位址的指標，如果方法呼叫失敗，則為 **null** 。</span><span class="sxs-lookup"><span data-stu-id="cf903-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf903-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="cf903-107">Return Value</span></span>  

 <span data-ttu-id="cf903-108">`S_OK` 如果方法呼叫成功，則為。否則， `S_FALSE` 與 `ppAssembly` 為 **null**。</span><span class="sxs-lookup"><span data-stu-id="cf903-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf903-109">備註</span><span class="sxs-lookup"><span data-stu-id="cf903-109">Remarks</span></span>  

 <span data-ttu-id="cf903-110">如果這個組件與其他組件已合併到單一容器組件內，這個方法會傳回該容器組件。</span><span class="sxs-lookup"><span data-stu-id="cf903-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="cf903-111">如需詳細資訊和術語，請參閱 [ICorDebugProcess6：： EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="cf903-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf903-112">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="cf903-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf903-113">需求</span><span class="sxs-lookup"><span data-stu-id="cf903-113">Requirements</span></span>  

 <span data-ttu-id="cf903-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cf903-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf903-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf903-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf903-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf903-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf903-117">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf903-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf903-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf903-118">See also</span></span>

- [<span data-ttu-id="cf903-119">ICorDebugAssembly3 介面</span><span class="sxs-lookup"><span data-stu-id="cf903-119">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="cf903-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="cf903-120">Debugging Interfaces</span></span>](debugging-interfaces.md)

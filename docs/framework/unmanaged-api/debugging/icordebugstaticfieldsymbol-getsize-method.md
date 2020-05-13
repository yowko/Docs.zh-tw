---
title: ICorDebugStaticFieldSymbol::GetSize 方法
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: e36c94bf411e75f915cca86aee74cdf161674d25
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379418"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="9fcb8-102">ICorDebugStaticFieldSymbol::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="9fcb8-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="9fcb8-103">取得靜態欄位的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="9fcb8-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fcb8-104">語法</span><span class="sxs-lookup"><span data-stu-id="9fcb8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fcb8-105">參數</span><span class="sxs-lookup"><span data-stu-id="9fcb8-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="9fcb8-106">[out] 欄位長度的指標。</span><span class="sxs-lookup"><span data-stu-id="9fcb8-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fcb8-107">備註</span><span class="sxs-lookup"><span data-stu-id="9fcb8-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9fcb8-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="9fcb8-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fcb8-109">需求</span><span class="sxs-lookup"><span data-stu-id="9fcb8-109">Requirements</span></span>  
 <span data-ttu-id="9fcb8-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9fcb8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fcb8-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9fcb8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fcb8-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fcb8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fcb8-113">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fcb8-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fcb8-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="9fcb8-114">See also</span></span>

- [<span data-ttu-id="9fcb8-115">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="9fcb8-115">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="9fcb8-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9fcb8-116">Debugging Interfaces</span></span>](debugging-interfaces.md)

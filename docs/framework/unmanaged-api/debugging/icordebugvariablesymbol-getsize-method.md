---
title: ICorDebugVariableSymbol：： GetSize 方法
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
ms.openlocfilehash: 61dad9522f9171166ca56a97e68b9a149d35e49a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120997"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="1f1ea-102">ICorDebugVariableSymbol：： GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="1f1ea-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="1f1ea-103">取得變數的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="1f1ea-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f1ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="1f1ea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f1ea-105">參數</span><span class="sxs-lookup"><span data-stu-id="1f1ea-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="1f1ea-106">32 位元不帶正負號的整數指標，這個整數包含變數的大小。</span><span class="sxs-lookup"><span data-stu-id="1f1ea-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f1ea-107">備註</span><span class="sxs-lookup"><span data-stu-id="1f1ea-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1f1ea-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="1f1ea-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f1ea-109">需求</span><span class="sxs-lookup"><span data-stu-id="1f1ea-109">Requirements</span></span>  
 <span data-ttu-id="1f1ea-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1f1ea-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f1ea-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f1ea-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f1ea-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f1ea-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f1ea-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f1ea-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f1ea-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="1f1ea-114">See also</span></span>

- [<span data-ttu-id="1f1ea-115">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="1f1ea-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="1f1ea-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1f1ea-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

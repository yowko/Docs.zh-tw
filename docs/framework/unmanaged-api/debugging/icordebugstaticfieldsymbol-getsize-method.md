---
title: ICorDebugStaticFieldSymbol::GetSize 方法
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9baa3632b6ede9ce45f34302611710344ed33761
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782599"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="ef444-102">ICorDebugStaticFieldSymbol::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="ef444-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="ef444-103">取得靜態欄位的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="ef444-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef444-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef444-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef444-105">參數</span><span class="sxs-lookup"><span data-stu-id="ef444-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="ef444-106">[out] 欄位長度的指標。</span><span class="sxs-lookup"><span data-stu-id="ef444-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef444-107">備註</span><span class="sxs-lookup"><span data-stu-id="ef444-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef444-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="ef444-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef444-109">需求</span><span class="sxs-lookup"><span data-stu-id="ef444-109">Requirements</span></span>  
 <span data-ttu-id="ef444-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ef444-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef444-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef444-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef444-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef444-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef444-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef444-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef444-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef444-114">See also</span></span>

- [<span data-ttu-id="ef444-115">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="ef444-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="ef444-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ef444-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugStaticFieldSymbol：： GetAddress 方法
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: 65761e48491b2a4c81ccd05b17d8723f71f52e5c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131802"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="4f7f6-102">ICorDebugStaticFieldSymbol：： GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="4f7f6-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="4f7f6-103">取得靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="4f7f6-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f7f6-104">語法</span><span class="sxs-lookup"><span data-stu-id="4f7f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f7f6-105">參數</span><span class="sxs-lookup"><span data-stu-id="4f7f6-105">Parameters</span></span>  
 <span data-ttu-id="4f7f6-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="4f7f6-106">pRVA</span></span>  
 <span data-ttu-id="4f7f6-107">[out] 靜態欄位的相對虛擬位址 (RVA) 指標。</span><span class="sxs-lookup"><span data-stu-id="4f7f6-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f7f6-108">備註</span><span class="sxs-lookup"><span data-stu-id="4f7f6-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f7f6-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="4f7f6-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f7f6-110">需求</span><span class="sxs-lookup"><span data-stu-id="4f7f6-110">Requirements</span></span>  
 <span data-ttu-id="4f7f6-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4f7f6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f7f6-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f7f6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f7f6-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f7f6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f7f6-114">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f7f6-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f7f6-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="4f7f6-115">See also</span></span>

- [<span data-ttu-id="4f7f6-116">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="4f7f6-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="4f7f6-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4f7f6-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

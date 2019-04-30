---
title: ICorDebugInstanceFieldSymbol::GetName 方法
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d23bf14fbb3d75534ac2d4a43eca0fbf3e994ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946415"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="8a60b-102">ICorDebugInstanceFieldSymbol::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="8a60b-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="8a60b-103">取得執行個體欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="8a60b-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a60b-104">語法</span><span class="sxs-lookup"><span data-stu-id="8a60b-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a60b-105">參數</span><span class="sxs-lookup"><span data-stu-id="8a60b-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="8a60b-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="8a60b-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8a60b-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="8a60b-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="8a60b-108">[out] 會儲存傳回的名稱之字元陣列。</span><span class="sxs-lookup"><span data-stu-id="8a60b-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a60b-109">備註</span><span class="sxs-lookup"><span data-stu-id="8a60b-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a60b-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="8a60b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a60b-111">需求</span><span class="sxs-lookup"><span data-stu-id="8a60b-111">Requirements</span></span>  
 <span data-ttu-id="8a60b-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a60b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a60b-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a60b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a60b-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a60b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a60b-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a60b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a60b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a60b-116">See also</span></span>

- [<span data-ttu-id="8a60b-117">ICorDebugInstanceFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="8a60b-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="8a60b-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8a60b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

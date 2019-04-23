---
title: ICorDebugInstanceFieldSymbol::GetOffset 方法
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8ea777755aebb59f3e865df26c38c74ef68ae31
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203869"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="8d0d5-102">ICorDebugInstanceFieldSymbol::GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="8d0d5-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="8d0d5-103">取得在父類別中此執行個體欄位之位元組的位移。</span><span class="sxs-lookup"><span data-stu-id="8d0d5-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d0d5-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d0d5-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d0d5-105">參數</span><span class="sxs-lookup"><span data-stu-id="8d0d5-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="8d0d5-106">此執行個體欄位在其父類別中的位移位元組數目。</span><span class="sxs-lookup"><span data-stu-id="8d0d5-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d0d5-107">備註</span><span class="sxs-lookup"><span data-stu-id="8d0d5-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d0d5-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="8d0d5-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d0d5-109">需求</span><span class="sxs-lookup"><span data-stu-id="8d0d5-109">Requirements</span></span>  
 <span data-ttu-id="8d0d5-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d0d5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d0d5-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d0d5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d0d5-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d0d5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d0d5-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d0d5-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d0d5-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d0d5-114">See also</span></span>

- [<span data-ttu-id="8d0d5-115">ICorDebugInstanceFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="8d0d5-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="8d0d5-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8d0d5-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

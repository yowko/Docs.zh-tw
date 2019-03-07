---
title: ICorDebugStaticFieldSymbol::GetAddress 方法
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a78df94fdc4190a43c80b0a8e3457f164e38eb00
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498051"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="926fc-102">ICorDebugStaticFieldSymbol::GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="926fc-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="926fc-103">取得靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="926fc-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="926fc-104">語法</span><span class="sxs-lookup"><span data-stu-id="926fc-104">Syntax</span></span>  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="926fc-105">參數</span><span class="sxs-lookup"><span data-stu-id="926fc-105">Parameters</span></span>  
 <span data-ttu-id="926fc-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="926fc-106">pRVA</span></span>  
 <span data-ttu-id="926fc-107">[out] 靜態欄位的相對虛擬位址 (RVA) 指標。</span><span class="sxs-lookup"><span data-stu-id="926fc-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="926fc-108">備註</span><span class="sxs-lookup"><span data-stu-id="926fc-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="926fc-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="926fc-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="926fc-110">需求</span><span class="sxs-lookup"><span data-stu-id="926fc-110">Requirements</span></span>  
 <span data-ttu-id="926fc-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="926fc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="926fc-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="926fc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="926fc-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="926fc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="926fc-114">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="926fc-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="926fc-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="926fc-115">See also</span></span>
- [<span data-ttu-id="926fc-116">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="926fc-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="926fc-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="926fc-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

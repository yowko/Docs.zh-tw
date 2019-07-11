---
title: ICorDebugSymbolProvider2::GetFrameProps 方法
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 274da030bbbb7c614709b5150f08f37ddf5aaf5a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771172"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="3b597-102">ICorDebugSymbolProvider2::GetFrameProps 方法</span><span class="sxs-lookup"><span data-stu-id="3b597-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="3b597-103">傳回某方法啟動相關的虛擬位址，以及被指定程式碼相關的虛擬位址的之父框架。</span><span class="sxs-lookup"><span data-stu-id="3b597-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b597-104">語法</span><span class="sxs-lookup"><span data-stu-id="3b597-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b597-105">參數</span><span class="sxs-lookup"><span data-stu-id="3b597-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="3b597-106">[in] 與程式碼相關的虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="3b597-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="3b597-107">[out] 指向該方法的啟動相關虛擬位址之指標。</span><span class="sxs-lookup"><span data-stu-id="3b597-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="3b597-108">[out] 指向該框架的啟動相關虛擬位址之指標。</span><span class="sxs-lookup"><span data-stu-id="3b597-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b597-109">備註</span><span class="sxs-lookup"><span data-stu-id="3b597-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b597-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="3b597-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b597-111">需求</span><span class="sxs-lookup"><span data-stu-id="3b597-111">Requirements</span></span>  
 <span data-ttu-id="3b597-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b597-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b597-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b597-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b597-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b597-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b597-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b597-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b597-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b597-116">See also</span></span>

- [<span data-ttu-id="3b597-117">ICorDebugSymbolProvider2 介面</span><span class="sxs-lookup"><span data-stu-id="3b597-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="3b597-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3b597-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugSymbolProvider2::GetFrameProps 方法
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 419e7bae5998679fafac48ebfd5b0673e0e4bac5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419077"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="3dd64-102">ICorDebugSymbolProvider2::GetFrameProps 方法</span><span class="sxs-lookup"><span data-stu-id="3dd64-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="3dd64-103">傳回某方法啟動相關的虛擬位址，以及被指定程式碼相關的虛擬位址的之父框架。</span><span class="sxs-lookup"><span data-stu-id="3dd64-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dd64-104">語法</span><span class="sxs-lookup"><span data-stu-id="3dd64-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3dd64-105">參數</span><span class="sxs-lookup"><span data-stu-id="3dd64-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="3dd64-106">[in] 與程式碼相關的虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="3dd64-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="3dd64-107">[out] 指向該方法的啟動相關虛擬位址之指標。</span><span class="sxs-lookup"><span data-stu-id="3dd64-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="3dd64-108">[out] 指向該框架的啟動相關虛擬位址之指標。</span><span class="sxs-lookup"><span data-stu-id="3dd64-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dd64-109">備註</span><span class="sxs-lookup"><span data-stu-id="3dd64-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3dd64-110">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="3dd64-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dd64-111">需求</span><span class="sxs-lookup"><span data-stu-id="3dd64-111">Requirements</span></span>  
 <span data-ttu-id="3dd64-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3dd64-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dd64-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3dd64-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dd64-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dd64-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dd64-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dd64-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd64-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3dd64-116">See Also</span></span>  
 [<span data-ttu-id="3dd64-117">ICorDebugSymbolProvider2 介面</span><span class="sxs-lookup"><span data-stu-id="3dd64-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="3dd64-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3dd64-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

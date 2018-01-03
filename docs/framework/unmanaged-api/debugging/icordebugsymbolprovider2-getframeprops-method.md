---
title: "ICorDebugSymbolProvider2::GetFrameProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f74ed8cdd7448d7ebeaa98108e84b42e86f428b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="f6cda-102">ICorDebugSymbolProvider2::GetFrameProps 方法</span><span class="sxs-lookup"><span data-stu-id="f6cda-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="f6cda-103">傳回某方法啟動相關的虛擬位址，以及被指定程式碼相關的虛擬位址的之父框架。</span><span class="sxs-lookup"><span data-stu-id="f6cda-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6cda-104">語法</span><span class="sxs-lookup"><span data-stu-id="f6cda-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6cda-105">參數</span><span class="sxs-lookup"><span data-stu-id="f6cda-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="f6cda-106">[in] 與程式碼相關的虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="f6cda-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="f6cda-107">[out] 指向該方法的啟動相關虛擬位址之指標。</span><span class="sxs-lookup"><span data-stu-id="f6cda-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="f6cda-108">[out] 指向該框架的啟動相關虛擬位址之指標。</span><span class="sxs-lookup"><span data-stu-id="f6cda-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6cda-109">備註</span><span class="sxs-lookup"><span data-stu-id="f6cda-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6cda-110">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="f6cda-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6cda-111">需求</span><span class="sxs-lookup"><span data-stu-id="f6cda-111">Requirements</span></span>  
 <span data-ttu-id="f6cda-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f6cda-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6cda-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6cda-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6cda-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6cda-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6cda-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6cda-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6cda-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="f6cda-116">See Also</span></span>  
 [<span data-ttu-id="f6cda-117">ICorDebugSymbolProvider2 介面</span><span class="sxs-lookup"><span data-stu-id="f6cda-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="f6cda-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f6cda-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

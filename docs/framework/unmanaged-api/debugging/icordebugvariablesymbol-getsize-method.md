---
title: ICorDebugVariableSymbol::GetSize 方法
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 027b3f773ff0ed0ca7bf9d193f97a3b060ea8494
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211838"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="6cdab-102">ICorDebugVariableSymbol::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="6cdab-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="6cdab-103">取得變數的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="6cdab-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cdab-104">語法</span><span class="sxs-lookup"><span data-stu-id="6cdab-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cdab-105">參數</span><span class="sxs-lookup"><span data-stu-id="6cdab-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="6cdab-106">32 位元不帶正負號的整數指標，這個整數包含變數的大小。</span><span class="sxs-lookup"><span data-stu-id="6cdab-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cdab-107">備註</span><span class="sxs-lookup"><span data-stu-id="6cdab-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6cdab-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="6cdab-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cdab-109">需求</span><span class="sxs-lookup"><span data-stu-id="6cdab-109">Requirements</span></span>  
 <span data-ttu-id="6cdab-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6cdab-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cdab-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6cdab-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6cdab-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cdab-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6cdab-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="6cdab-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6cdab-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cdab-114">See also</span></span>

- [<span data-ttu-id="6cdab-115">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="6cdab-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="6cdab-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6cdab-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

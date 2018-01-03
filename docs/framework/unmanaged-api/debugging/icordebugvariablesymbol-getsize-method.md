---
title: ICorDebugVariableSymbol::GetSize Method
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99cba63edd56e0d27d5f558a77ee54ebf2629446
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="4bf43-102">ICorDebugVariableSymbol::GetSize Method</span><span class="sxs-lookup"><span data-stu-id="4bf43-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="4bf43-103">取得變數的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="4bf43-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bf43-104">語法</span><span class="sxs-lookup"><span data-stu-id="4bf43-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4bf43-105">參數</span><span class="sxs-lookup"><span data-stu-id="4bf43-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="4bf43-106">32 位元不帶正負號的整數指標，這個整數包含變數的大小。</span><span class="sxs-lookup"><span data-stu-id="4bf43-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bf43-107">備註</span><span class="sxs-lookup"><span data-stu-id="4bf43-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4bf43-108">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="4bf43-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bf43-109">需求</span><span class="sxs-lookup"><span data-stu-id="4bf43-109">Requirements</span></span>  
 <span data-ttu-id="4bf43-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4bf43-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bf43-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4bf43-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4bf43-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4bf43-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bf43-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bf43-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bf43-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="4bf43-114">See Also</span></span>  
 [<span data-ttu-id="4bf43-115">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="4bf43-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="4bf43-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4bf43-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

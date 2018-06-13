---
title: ICorDebugProcess6::GetCode 方法
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 572b279ddfdb1fb0eb9da4b0d1f8c2cb12c8a46b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420159"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="cb7f2-102">ICorDebugProcess6::GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="cb7f2-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="cb7f2-103">取得特定程式碼位址之 Managed 程式碼的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cb7f2-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb7f2-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb7f2-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb7f2-105">參數</span><span class="sxs-lookup"><span data-stu-id="cb7f2-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="cb7f2-106">[in]A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值，指定 managed 程式碼區段的起始位址。</span><span class="sxs-lookup"><span data-stu-id="cb7f2-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="cb7f2-107">[out]代表 managed 程式碼的區段"ICorDebugCode 」 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="cb7f2-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb7f2-108">備註</span><span class="sxs-lookup"><span data-stu-id="cb7f2-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb7f2-109">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="cb7f2-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb7f2-110">需求</span><span class="sxs-lookup"><span data-stu-id="cb7f2-110">Requirements</span></span>  
 <span data-ttu-id="cb7f2-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb7f2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb7f2-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb7f2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb7f2-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb7f2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb7f2-114">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb7f2-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb7f2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb7f2-115">See Also</span></span>  
 [<span data-ttu-id="cb7f2-116">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="cb7f2-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="cb7f2-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="cb7f2-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

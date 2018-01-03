---
title: "ICorDebugProcess6::DecodeEvent 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 753dce06d9481165bd2f0f1e49fe3c50fc6b3c40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="be270-102">ICorDebugProcess6::DecodeEvent 方法</span><span class="sxs-lookup"><span data-stu-id="be270-102">ICorDebugProcess6::DecodeEvent Method</span></span>
<span data-ttu-id="be270-103">對已封裝在特殊設計之原生例外狀況偵錯事件承載中的 Managed 偵錯事件進行解碼。</span><span class="sxs-lookup"><span data-stu-id="be270-103">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be270-104">語法</span><span class="sxs-lookup"><span data-stu-id="be270-104">Syntax</span></span>  
  
```  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,   
        [in] DWORD dwThreadId,   
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be270-105">參數</span><span class="sxs-lookup"><span data-stu-id="be270-105">Parameters</span></span>  
 `pRecord`  
 <span data-ttu-id="be270-106">[in] 原生例外狀況偵錯事件中的位元組陣列指標，該事件包含 Managed 偵錯事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="be270-106">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="be270-107">[in] `pRecord` 位元組陣列中的項目數。</span><span class="sxs-lookup"><span data-stu-id="be270-107">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="be270-108">[in]A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)列舉的成員，指定的 unmanaged 偵錯事件格式。</span><span class="sxs-lookup"><span data-stu-id="be270-108">[in] A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="be270-109">[in] 相依於目標架構並指定偵錯事件之其他資訊的位元欄位。</span><span class="sxs-lookup"><span data-stu-id="be270-109">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="be270-110">適用於 Windows 系統，它可以是隸屬[CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="be270-110">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="be270-111">[in] 擲回例外狀況之執行緒的作業系統識別項。</span><span class="sxs-lookup"><span data-stu-id="be270-111">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="be270-112">[out]位址指標[ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)物件，代表已解碼的 managed 偵錯事件。</span><span class="sxs-lookup"><span data-stu-id="be270-112">[out] A pointer to the address of an [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be270-113">備註</span><span class="sxs-lookup"><span data-stu-id="be270-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be270-114">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="be270-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be270-115">需求</span><span class="sxs-lookup"><span data-stu-id="be270-115">Requirements</span></span>  
 <span data-ttu-id="be270-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be270-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be270-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be270-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be270-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be270-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be270-119">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be270-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be270-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="be270-120">See Also</span></span>  
 [<span data-ttu-id="be270-121">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="be270-121">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="be270-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="be270-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

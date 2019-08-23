---
title: ICorDebugProcess6::DecodeEvent 方法
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f81c513447b7c63fb16ff20ae6f83c3e6ef359b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964048"
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="54c96-102">ICorDebugProcess6::DecodeEvent 方法</span><span class="sxs-lookup"><span data-stu-id="54c96-102">ICorDebugProcess6::DecodeEvent Method</span></span>
<span data-ttu-id="54c96-103">對已封裝在特殊設計之原生例外狀況偵錯事件承載中的 Managed 偵錯事件進行解碼。</span><span class="sxs-lookup"><span data-stu-id="54c96-103">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54c96-104">語法</span><span class="sxs-lookup"><span data-stu-id="54c96-104">Syntax</span></span>  
  
```cpp  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,   
        [in] DWORD dwThreadId,   
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54c96-105">參數</span><span class="sxs-lookup"><span data-stu-id="54c96-105">Parameters</span></span>  
 `pRecord`  
 <span data-ttu-id="54c96-106">[in] 原生例外狀況偵錯事件中的位元組陣列指標，該事件包含 Managed 偵錯事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="54c96-106">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="54c96-107">[in] `pRecord` 位元組陣列中的項目數。</span><span class="sxs-lookup"><span data-stu-id="54c96-107">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="54c96-108">在指定非受控 debug 事件格式的[CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)列舉成員。</span><span class="sxs-lookup"><span data-stu-id="54c96-108">[in] A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="54c96-109">[in] 相依於目標架構並指定偵錯事件之其他資訊的位元欄位。</span><span class="sxs-lookup"><span data-stu-id="54c96-109">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="54c96-110">對於 Windows 系統, 它可以是[CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)列舉的成員。</span><span class="sxs-lookup"><span data-stu-id="54c96-110">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="54c96-111">[in] 擲回例外狀況之執行緒的作業系統識別項。</span><span class="sxs-lookup"><span data-stu-id="54c96-111">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="54c96-112">脫銷[ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)物件位址的指標, 表示已解碼的 managed 偵錯工具事件。</span><span class="sxs-lookup"><span data-stu-id="54c96-112">[out] A pointer to the address of an [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54c96-113">備註</span><span class="sxs-lookup"><span data-stu-id="54c96-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54c96-114">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="54c96-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54c96-115">需求</span><span class="sxs-lookup"><span data-stu-id="54c96-115">Requirements</span></span>  
 <span data-ttu-id="54c96-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="54c96-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54c96-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54c96-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54c96-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54c96-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54c96-119">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54c96-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c96-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54c96-120">See also</span></span>

- [<span data-ttu-id="54c96-121">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="54c96-121">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="54c96-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="54c96-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

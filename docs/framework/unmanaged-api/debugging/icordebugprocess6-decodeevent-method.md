---
title: ICorDebugProcess6::DecodeEvent 方法
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: ed75b3c5657fed805f187285a576b81598be331c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690274"
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="60aaf-102">ICorDebugProcess6::DecodeEvent 方法</span><span class="sxs-lookup"><span data-stu-id="60aaf-102">ICorDebugProcess6::DecodeEvent Method</span></span>

<span data-ttu-id="60aaf-103">對已封裝在特殊設計之原生例外狀況偵錯事件承載中的 Managed 偵錯事件進行解碼。</span><span class="sxs-lookup"><span data-stu-id="60aaf-103">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60aaf-104">語法</span><span class="sxs-lookup"><span data-stu-id="60aaf-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="60aaf-105">參數</span><span class="sxs-lookup"><span data-stu-id="60aaf-105">Parameters</span></span>  

 `pRecord`  
 <span data-ttu-id="60aaf-106">[in] 原生例外狀況偵錯事件中的位元組陣列指標，該事件包含 Managed 偵錯事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="60aaf-106">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="60aaf-107">[in] `pRecord` 位元組陣列中的項目數。</span><span class="sxs-lookup"><span data-stu-id="60aaf-107">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="60aaf-108">在 [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) 列舉成員，指定未受管理的偵錯工具事件的格式。</span><span class="sxs-lookup"><span data-stu-id="60aaf-108">[in] A [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="60aaf-109">[in] 相依於目標架構並指定偵錯事件之其他資訊的位元欄位。</span><span class="sxs-lookup"><span data-stu-id="60aaf-109">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="60aaf-110">對於 Windows 系統而言，它可以是 [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) 列舉的成員。</span><span class="sxs-lookup"><span data-stu-id="60aaf-110">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="60aaf-111">[in] 擲回例外狀況之執行緒的作業系統識別項。</span><span class="sxs-lookup"><span data-stu-id="60aaf-111">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="60aaf-112">擴展 [ICorDebugDebugEvent](icordebugdebugevent-interface.md) 物件位址的指標，該物件表示已解碼的 managed 偵錯工具事件。</span><span class="sxs-lookup"><span data-stu-id="60aaf-112">[out] A pointer to the address of an [ICorDebugDebugEvent](icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60aaf-113">備註</span><span class="sxs-lookup"><span data-stu-id="60aaf-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60aaf-114">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="60aaf-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60aaf-115">需求</span><span class="sxs-lookup"><span data-stu-id="60aaf-115">Requirements</span></span>  

 <span data-ttu-id="60aaf-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="60aaf-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60aaf-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60aaf-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60aaf-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60aaf-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60aaf-119">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60aaf-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60aaf-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60aaf-120">See also</span></span>

- [<span data-ttu-id="60aaf-121">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="60aaf-121">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="60aaf-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="60aaf-122">Debugging Interfaces</span></span>](debugging-interfaces.md)

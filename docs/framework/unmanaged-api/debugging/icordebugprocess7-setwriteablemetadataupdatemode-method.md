---
title: "ICorDebugProcess7::SetWriteableMetadataUpdateMode 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e901fd623893b9c03e1b5835adc72c6bd225ead4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="bdfef-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode 方法</span><span class="sxs-lookup"><span data-stu-id="bdfef-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="bdfef-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="bdfef-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="bdfef-104">設定偵錯工具如何處理對目標處理序中之中繼資料的記憶體中更新。</span><span class="sxs-lookup"><span data-stu-id="bdfef-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdfef-105">語法</span><span class="sxs-lookup"><span data-stu-id="bdfef-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bdfef-106">參數</span><span class="sxs-lookup"><span data-stu-id="bdfef-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="bdfef-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)列舉值，指定是否顯示在目標處理序的中繼資料的記憶體中更新 (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) 或不可見 (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="bdfef-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdfef-108">備註</span><span class="sxs-lookup"><span data-stu-id="bdfef-108">Remarks</span></span>  
 <span data-ttu-id="bdfef-109">對目標處理序之中繼資料的更新可能是透過 [編輯後繼續]、分析工具或 <xref:System.Reflection.Emit?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="bdfef-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdfef-110">需求</span><span class="sxs-lookup"><span data-stu-id="bdfef-110">Requirements</span></span>  
 <span data-ttu-id="bdfef-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bdfef-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdfef-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdfef-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdfef-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdfef-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdfef-114">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdfef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdfef-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="bdfef-115">See Also</span></span>  
 [<span data-ttu-id="bdfef-116">ICorDebugProcess7 介面</span><span class="sxs-lookup"><span data-stu-id="bdfef-116">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 [<span data-ttu-id="bdfef-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="bdfef-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

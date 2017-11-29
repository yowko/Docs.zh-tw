---
title: "ICorDebugProcess7::SetWriteableMetadataUpdateMode 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location: mscordbi.dll
api_type: COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 635792962e259f181a1ff3e0c46438951e4223db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="24d2e-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode 方法</span><span class="sxs-lookup"><span data-stu-id="24d2e-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="24d2e-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="24d2e-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="24d2e-104">設定偵錯工具如何處理對目標處理序中之中繼資料的記憶體中更新。</span><span class="sxs-lookup"><span data-stu-id="24d2e-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24d2e-105">語法</span><span class="sxs-lookup"><span data-stu-id="24d2e-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24d2e-106">參數</span><span class="sxs-lookup"><span data-stu-id="24d2e-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="24d2e-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)列舉值，指定是否顯示在目標處理序的中繼資料的記憶體中更新 (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) 或不可見 (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="24d2e-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24d2e-108">備註</span><span class="sxs-lookup"><span data-stu-id="24d2e-108">Remarks</span></span>  
 <span data-ttu-id="24d2e-109">對目標處理序之中繼資料的更新可能是透過 [編輯後繼續]、分析工具或 <xref:System.Reflection.Emit?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="24d2e-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24d2e-110">需求</span><span class="sxs-lookup"><span data-stu-id="24d2e-110">Requirements</span></span>  
 <span data-ttu-id="24d2e-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="24d2e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24d2e-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24d2e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24d2e-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24d2e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24d2e-114">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24d2e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24d2e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24d2e-115">See Also</span></span>  
 [<span data-ttu-id="24d2e-116">ICorDebugProcess7 介面</span><span class="sxs-lookup"><span data-stu-id="24d2e-116">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 [<span data-ttu-id="24d2e-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="24d2e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

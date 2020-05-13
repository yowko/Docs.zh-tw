---
title: ICorDebugProcess7::SetWriteableMetadataUpdateMode 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: 6de75e1e27660ac91bd6320a501db47f3b055fb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212252"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="1e9cf-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode 方法</span><span class="sxs-lookup"><span data-stu-id="1e9cf-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="1e9cf-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="1e9cf-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1e9cf-104">設定偵錯工具如何處理對目標處理序中之中繼資料的記憶體中更新。</span><span class="sxs-lookup"><span data-stu-id="1e9cf-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e9cf-105">語法</span><span class="sxs-lookup"><span data-stu-id="1e9cf-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e9cf-106">參數</span><span class="sxs-lookup"><span data-stu-id="1e9cf-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="1e9cf-107">[WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md)列舉值，指定目標進程中的中繼資料的記憶體中更新是否可見（）， `WriteableMetadataUpdateMode::AlwaysShowUpdates` 或不會 `WriteableMetadataUpdateMode::LegacyCompatPolicy` 對偵錯工具顯示（）。</span><span class="sxs-lookup"><span data-stu-id="1e9cf-107">A [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e9cf-108">備註</span><span class="sxs-lookup"><span data-stu-id="1e9cf-108">Remarks</span></span>  
 <span data-ttu-id="1e9cf-109">對目標處理序之中繼資料的更新可能是透過 [編輯後繼續]、分析工具或 <xref:System.Reflection.Emit?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1e9cf-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e9cf-110">需求</span><span class="sxs-lookup"><span data-stu-id="1e9cf-110">Requirements</span></span>  
 <span data-ttu-id="1e9cf-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1e9cf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e9cf-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e9cf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e9cf-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e9cf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e9cf-114">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e9cf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e9cf-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="1e9cf-115">See also</span></span>

- [<span data-ttu-id="1e9cf-116">ICorDebugProcess7 介面</span><span class="sxs-lookup"><span data-stu-id="1e9cf-116">ICorDebugProcess7 Interface</span></span>](icordebugprocess7-interface.md)
- [<span data-ttu-id="1e9cf-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1e9cf-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

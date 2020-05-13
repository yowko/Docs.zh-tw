---
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords 方法
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: b7d26fa80a7a8ebe7b4606b914c8cd09c52df1e4
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379628"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="ca215-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords 方法</span><span class="sxs-lookup"><span data-stu-id="ca215-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="ca215-103">取得所有合併組件的符號記錄。</span><span class="sxs-lookup"><span data-stu-id="ca215-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca215-104">語法</span><span class="sxs-lookup"><span data-stu-id="ca215-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca215-105">參數</span><span class="sxs-lookup"><span data-stu-id="ca215-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="ca215-106">[in] 要求的符號記錄數目。</span><span class="sxs-lookup"><span data-stu-id="ca215-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="ca215-107">[out] 方法所擷取之符號記錄數的指標。</span><span class="sxs-lookup"><span data-stu-id="ca215-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="ca215-108">[ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)物件陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="ca215-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca215-109">備註</span><span class="sxs-lookup"><span data-stu-id="ca215-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca215-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="ca215-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca215-111">需求</span><span class="sxs-lookup"><span data-stu-id="ca215-111">Requirements</span></span>  
 <span data-ttu-id="ca215-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ca215-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca215-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca215-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca215-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca215-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca215-115">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca215-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca215-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="ca215-116">See also</span></span>

- [<span data-ttu-id="ca215-117">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="ca215-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="ca215-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ca215-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

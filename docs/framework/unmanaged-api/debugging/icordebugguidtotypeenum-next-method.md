---
title: ICorDebugGuidToTypeEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
ms.openlocfilehash: 68f548705213da7d715ae569116abae0cd24129d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705653"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="aa55d-102">ICorDebugGuidToTypeEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="aa55d-102">ICorDebugGuidToTypeEnum::Next Method</span></span>

<span data-ttu-id="aa55d-103">取得將 Guid 對應至類型資訊的指定 [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) 實例數目。</span><span class="sxs-lookup"><span data-stu-id="aa55d-103">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa55d-104">語法</span><span class="sxs-lookup"><span data-stu-id="aa55d-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa55d-105">參數</span><span class="sxs-lookup"><span data-stu-id="aa55d-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="aa55d-106">在要抓取的 GUID 對類型對應物件數目。</span><span class="sxs-lookup"><span data-stu-id="aa55d-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="aa55d-107">擴展指標的陣列，每個指標都會指向 [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) 物件，該物件會將 Windows 執行階段 GUID 對應至其對應的 ICorDebugType 物件。</span><span class="sxs-lookup"><span data-stu-id="aa55d-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="aa55d-108">擴展實際傳回的 [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) 物件數目指標 `values` 。</span><span class="sxs-lookup"><span data-stu-id="aa55d-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa55d-109">備註</span><span class="sxs-lookup"><span data-stu-id="aa55d-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa55d-110">需求</span><span class="sxs-lookup"><span data-stu-id="aa55d-110">Requirements</span></span>  

 <span data-ttu-id="aa55d-111">**平臺：** Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="aa55d-111">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="aa55d-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa55d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa55d-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa55d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa55d-114">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa55d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa55d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa55d-115">See also</span></span>

- [<span data-ttu-id="aa55d-116">ICorDebugGuidToTypeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="aa55d-116">ICorDebugGuidToTypeEnum Interface</span></span>](icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="aa55d-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="aa55d-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

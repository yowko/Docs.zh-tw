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
ms.openlocfilehash: 76cab0b8b5f16f24c62e31be2707c95c7e557034
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777634"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="7e406-102">ICorDebugGuidToTypeEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="7e406-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="7e406-103">取得將 Guid 對應至類型資訊的指定[CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md)實例數目。</span><span class="sxs-lookup"><span data-stu-id="7e406-103">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e406-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e406-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e406-105">參數</span><span class="sxs-lookup"><span data-stu-id="7e406-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7e406-106">在要抓取的 GUID 型別對應物件的數目。</span><span class="sxs-lookup"><span data-stu-id="7e406-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="7e406-107">脫銷指標的陣列，其中每一個都會指向[CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md)物件，它會將 Windows 執行階段 GUID 對應至其相對應的 ICorDebugType 物件。</span><span class="sxs-lookup"><span data-stu-id="7e406-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7e406-108">脫銷`values`中實際傳回之[CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md)物件數目的指標。</span><span class="sxs-lookup"><span data-stu-id="7e406-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e406-109">備註</span><span class="sxs-lookup"><span data-stu-id="7e406-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e406-110">需求</span><span class="sxs-lookup"><span data-stu-id="7e406-110">Requirements</span></span>  
 <span data-ttu-id="7e406-111">**平臺：** Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="7e406-111">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="7e406-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e406-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e406-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e406-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e406-114">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e406-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e406-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="7e406-115">See also</span></span>

- [<span data-ttu-id="7e406-116">ICorDebugGuidToTypeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="7e406-116">ICorDebugGuidToTypeEnum Interface</span></span>](icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="7e406-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7e406-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

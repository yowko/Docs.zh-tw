---
title: ICorDebugAssembly::GetName 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type:
- apiref
ms.openlocfilehash: 3794a3b308bd5c96a38337d8b81e61167e4dc988
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734045"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="5deb1-102">ICorDebugAssembly::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="5deb1-102">ICorDebugAssembly::GetName Method</span></span>

<span data-ttu-id="5deb1-103">取得這個實例所表示之元件的名稱 `ICorDebugAssembly` 。</span><span class="sxs-lookup"><span data-stu-id="5deb1-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5deb1-104">語法</span><span class="sxs-lookup"><span data-stu-id="5deb1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5deb1-105">參數</span><span class="sxs-lookup"><span data-stu-id="5deb1-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="5deb1-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="5deb1-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5deb1-107">擴展指定名稱實際長度的整數指標。</span><span class="sxs-lookup"><span data-stu-id="5deb1-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="5deb1-108">擴展儲存名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="5deb1-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5deb1-109">備註</span><span class="sxs-lookup"><span data-stu-id="5deb1-109">Remarks</span></span>  

 <span data-ttu-id="5deb1-110">方法會傳回 `GetName` 元件的完整路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="5deb1-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5deb1-111">需求</span><span class="sxs-lookup"><span data-stu-id="5deb1-111">Requirements</span></span>  

 <span data-ttu-id="5deb1-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5deb1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5deb1-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5deb1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5deb1-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5deb1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5deb1-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5deb1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

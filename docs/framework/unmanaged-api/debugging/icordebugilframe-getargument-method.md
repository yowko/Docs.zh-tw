---
title: ICorDebugILFrame::GetArgument 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
ms.openlocfilehash: d715f5842bb7f75da5311d34bf7d4596f0801a92
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210276"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="1aa4c-102">ICorDebugILFrame::GetArgument 方法</span><span class="sxs-lookup"><span data-stu-id="1aa4c-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="1aa4c-103">取得此 Microsoft 中繼語言（MSIL）堆疊框架中指定之引數的值。</span><span class="sxs-lookup"><span data-stu-id="1aa4c-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aa4c-104">語法</span><span class="sxs-lookup"><span data-stu-id="1aa4c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1aa4c-105">參數</span><span class="sxs-lookup"><span data-stu-id="1aa4c-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="1aa4c-106">在這個 MSIL 堆疊框架中引數的索引。</span><span class="sxs-lookup"><span data-stu-id="1aa4c-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="1aa4c-107">[out] 代表擷取值之 ICorDebugValue 物件的位置指標。</span><span class="sxs-lookup"><span data-stu-id="1aa4c-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1aa4c-108">備註</span><span class="sxs-lookup"><span data-stu-id="1aa4c-108">Remarks</span></span>  
 <span data-ttu-id="1aa4c-109">`GetArgument`方法可以在 MSIL 堆疊框架或即時（JIT）編譯的框架中使用。</span><span class="sxs-lookup"><span data-stu-id="1aa4c-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aa4c-110">需求</span><span class="sxs-lookup"><span data-stu-id="1aa4c-110">Requirements</span></span>  
 <span data-ttu-id="1aa4c-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1aa4c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aa4c-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1aa4c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1aa4c-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1aa4c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1aa4c-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aa4c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
title: ICorDebugILFrame::GetLocalVariable 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
ms.openlocfilehash: 85f06b49aab1f1d1745bd7e359ed311c2ba1e44d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130973"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="5bd67-102">ICorDebugILFrame::GetLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="5bd67-102">ICorDebugILFrame::GetLocalVariable Method</span></span>
<span data-ttu-id="5bd67-103">取得此 Microsoft 中繼語言（MSIL）堆疊框架中指定之區域變數的值。</span><span class="sxs-lookup"><span data-stu-id="5bd67-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bd67-104">語法</span><span class="sxs-lookup"><span data-stu-id="5bd67-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bd67-105">參數</span><span class="sxs-lookup"><span data-stu-id="5bd67-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="5bd67-106">在這個 MSIL 堆疊框架中區域變數的索引。</span><span class="sxs-lookup"><span data-stu-id="5bd67-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="5bd67-107">脫銷ICorDebugValue 物件位址的指標，表示已抓取的值。</span><span class="sxs-lookup"><span data-stu-id="5bd67-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bd67-108">備註</span><span class="sxs-lookup"><span data-stu-id="5bd67-108">Remarks</span></span>  
 <span data-ttu-id="5bd67-109">`GetLocalVariable` 方法可以在 MSIL 堆疊框架或即時（JIT）編譯的框架中使用。</span><span class="sxs-lookup"><span data-stu-id="5bd67-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bd67-110">需求</span><span class="sxs-lookup"><span data-stu-id="5bd67-110">Requirements</span></span>  
 <span data-ttu-id="5bd67-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5bd67-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bd67-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5bd67-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5bd67-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bd67-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bd67-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bd67-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

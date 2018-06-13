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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1653913ca7410728f0f90a546f613a9d8b88be7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414049"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="d5c63-102">ICorDebugILFrame::GetArgument 方法</span><span class="sxs-lookup"><span data-stu-id="d5c63-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="d5c63-103">此 Microsoft intermediate language (MSIL) 堆疊框架中取得指定的引數的值。</span><span class="sxs-lookup"><span data-stu-id="d5c63-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5c63-104">語法</span><span class="sxs-lookup"><span data-stu-id="d5c63-104">Syntax</span></span>  
  
```  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5c63-105">參數</span><span class="sxs-lookup"><span data-stu-id="d5c63-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="d5c63-106">[in]此 MSIL 堆疊框架中的引數索引。</span><span class="sxs-lookup"><span data-stu-id="d5c63-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="d5c63-107">[out]ICorDebugValue 物件，代表擷取的值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="d5c63-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5c63-108">備註</span><span class="sxs-lookup"><span data-stu-id="d5c63-108">Remarks</span></span>  
 <span data-ttu-id="d5c63-109">`GetArgument`方法可以用在 MSIL 堆疊框架中或在 just-in-time (JIT) 編譯的框架中。</span><span class="sxs-lookup"><span data-stu-id="d5c63-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5c63-110">需求</span><span class="sxs-lookup"><span data-stu-id="d5c63-110">Requirements</span></span>  
 <span data-ttu-id="d5c63-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d5c63-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5c63-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5c63-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5c63-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5c63-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5c63-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5c63-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

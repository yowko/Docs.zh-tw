---
title: ICorDebugClass::GetModule 方法
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetModule
helpviewer_keywords:
- GetModule method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetModule method [.NET Framework debugging]
ms.assetid: 87029cc4-e5e1-42d5-8b98-655bb7ece520
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c52795251b5cacebe749b1eedf918f8b20497796
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402893"
---
# <a name="icordebugclassgetmodule-method"></a><span data-ttu-id="b4222-102">ICorDebugClass::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="b4222-102">ICorDebugClass::GetModule Method</span></span>
<span data-ttu-id="b4222-103">取得定義此類別的模組。</span><span class="sxs-lookup"><span data-stu-id="b4222-103">Gets the module that defines this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4222-104">語法</span><span class="sxs-lookup"><span data-stu-id="b4222-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule    **pModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4222-105">參數</span><span class="sxs-lookup"><span data-stu-id="b4222-105">Parameters</span></span>  
 `pModule`  
 <span data-ttu-id="b4222-106">[out]ICorDebugModule 物件，表示這個類別定義所在模組的位址指標。</span><span class="sxs-lookup"><span data-stu-id="b4222-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this class is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4222-107">需求</span><span class="sxs-lookup"><span data-stu-id="b4222-107">Requirements</span></span>  
 <span data-ttu-id="b4222-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4222-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4222-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4222-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4222-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4222-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4222-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4222-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

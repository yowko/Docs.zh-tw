---
title: ICorDebugModule::GetClassFromToken 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetClassFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetClassFromToken
helpviewer_keywords:
- GetClassFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetClassFromToken method [.NET Framework debugging]
ms.assetid: 622a4d3c-0425-4c54-a7e4-0735377cdad2
topic_type:
- apiref
ms.openlocfilehash: 790999093f874a4d81dd5db74ef012b1d997a12f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109652"
---
# <a name="icordebugmodulegetclassfromtoken-method"></a><span data-ttu-id="49fdf-102">ICorDebugModule::GetClassFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="49fdf-102">ICorDebugModule::GetClassFromToken Method</span></span>
<span data-ttu-id="49fdf-103">取得元資料標記所指定的類別。</span><span class="sxs-lookup"><span data-stu-id="49fdf-103">Gets the class specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49fdf-104">語法</span><span class="sxs-lookup"><span data-stu-id="49fdf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  mdTypeDef        typeDef,  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49fdf-105">參數</span><span class="sxs-lookup"><span data-stu-id="49fdf-105">Parameters</span></span>  
 `typedef`  
 <span data-ttu-id="49fdf-106">在參考類別之中繼資料的 `mdTypeDef` 中繼資料 token。</span><span class="sxs-lookup"><span data-stu-id="49fdf-106">[in] An `mdTypeDef` metadata token that references the metadata of a class.</span></span>  
  
 `ppClass`  
 <span data-ttu-id="49fdf-107">脫銷表示類別之 ICorDebugClass 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="49fdf-107">[out] A pointer to the address of an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49fdf-108">需求</span><span class="sxs-lookup"><span data-stu-id="49fdf-108">Requirements</span></span>  
 <span data-ttu-id="49fdf-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49fdf-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49fdf-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49fdf-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49fdf-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49fdf-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49fdf-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49fdf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

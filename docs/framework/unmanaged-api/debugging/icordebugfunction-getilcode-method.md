---
title: ICorDebugFunction::GetILCode 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac34fbca56c8a0f00ee3a7e0f898b8ee03287b11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412281"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="80593-102">ICorDebugFunction::GetILCode 方法</span><span class="sxs-lookup"><span data-stu-id="80593-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="80593-103">取得表示這個 ICorDebugFunction 物件相關聯的 Microsoft intermediate language (MSIL) 程式碼 ICorDebugCode 執行個體。</span><span class="sxs-lookup"><span data-stu-id="80593-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80593-104">語法</span><span class="sxs-lookup"><span data-stu-id="80593-104">Syntax</span></span>  
  
```  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80593-105">參數</span><span class="sxs-lookup"><span data-stu-id="80593-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="80593-106">[out]指標`ICorDebugCode`執行個體，則為 null，如果函式並不是編譯成 MSIL。</span><span class="sxs-lookup"><span data-stu-id="80593-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80593-107">備註</span><span class="sxs-lookup"><span data-stu-id="80593-107">Remarks</span></span>  
 <span data-ttu-id="80593-108">如果已在這個函式，允許編輯後繼續`GetILCode`方法會取得對應到此函式已編輯版本的 common language runtime (CLR) 中的程式碼的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="80593-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80593-109">需求</span><span class="sxs-lookup"><span data-stu-id="80593-109">Requirements</span></span>  
 <span data-ttu-id="80593-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="80593-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80593-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80593-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80593-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80593-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80593-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80593-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

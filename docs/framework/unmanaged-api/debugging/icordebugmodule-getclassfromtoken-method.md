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
ms.openlocfilehash: f8a56dcf03748c6582bce07fc379113c5cdddd11
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212592"
---
# <a name="icordebugmodulegetclassfromtoken-method"></a><span data-ttu-id="98c76-102">ICorDebugModule::GetClassFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="98c76-102">ICorDebugModule::GetClassFromToken Method</span></span>
<span data-ttu-id="98c76-103">取得元資料標記所指定的類別。</span><span class="sxs-lookup"><span data-stu-id="98c76-103">Gets the class specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98c76-104">語法</span><span class="sxs-lookup"><span data-stu-id="98c76-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  mdTypeDef        typeDef,  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98c76-105">參數</span><span class="sxs-lookup"><span data-stu-id="98c76-105">Parameters</span></span>  
 `typedef`  
 <span data-ttu-id="98c76-106">在`mdTypeDef`參考類別中繼資料的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="98c76-106">[in] An `mdTypeDef` metadata token that references the metadata of a class.</span></span>  
  
 `ppClass`  
 <span data-ttu-id="98c76-107">脫銷表示類別之 ICorDebugClass 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="98c76-107">[out] A pointer to the address of an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98c76-108">需求</span><span class="sxs-lookup"><span data-stu-id="98c76-108">Requirements</span></span>  
 <span data-ttu-id="98c76-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98c76-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98c76-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98c76-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98c76-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98c76-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98c76-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98c76-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

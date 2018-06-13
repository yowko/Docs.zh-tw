---
title: ICorDebugModule::GetBaseAddress 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetBaseAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10e7da7711cd63579589fda416d0d3a4f777eefe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412536"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="2de5d-102">ICorDebugModule::GetBaseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="2de5d-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="2de5d-103">取得模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="2de5d-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2de5d-104">語法</span><span class="sxs-lookup"><span data-stu-id="2de5d-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2de5d-105">參數</span><span class="sxs-lookup"><span data-stu-id="2de5d-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="2de5d-106">[out]A`CORDB_ADDRESS`指定模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="2de5d-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2de5d-107">備註</span><span class="sxs-lookup"><span data-stu-id="2de5d-107">Remarks</span></span>  
 <span data-ttu-id="2de5d-108">如果模組是原生映像 （亦即，如果模組已由原生映像產生器 NGen.exe 產生），其基底地址將會是零。</span><span class="sxs-lookup"><span data-stu-id="2de5d-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2de5d-109">需求</span><span class="sxs-lookup"><span data-stu-id="2de5d-109">Requirements</span></span>  
 <span data-ttu-id="2de5d-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2de5d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2de5d-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2de5d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2de5d-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2de5d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2de5d-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2de5d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2de5d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2de5d-114">See Also</span></span>  
    
 

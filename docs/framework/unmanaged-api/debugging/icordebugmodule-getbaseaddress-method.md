---
title: "ICorDebugModule::GetBaseAddress 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetBaseAddress
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a3e6a613fc272dc20089856b479b62afd5bf2487
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="44778-102">ICorDebugModule::GetBaseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="44778-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="44778-103">取得模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="44778-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44778-104">語法</span><span class="sxs-lookup"><span data-stu-id="44778-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44778-105">參數</span><span class="sxs-lookup"><span data-stu-id="44778-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="44778-106">[out]A`CORDB_ADDRESS`指定模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="44778-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44778-107">備註</span><span class="sxs-lookup"><span data-stu-id="44778-107">Remarks</span></span>  
 <span data-ttu-id="44778-108">如果模組是原生映像 （亦即，如果模組已由原生映像產生器 NGen.exe 產生），其基底地址將會是零。</span><span class="sxs-lookup"><span data-stu-id="44778-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44778-109">需求</span><span class="sxs-lookup"><span data-stu-id="44778-109">Requirements</span></span>  
 <span data-ttu-id="44778-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44778-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44778-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44778-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44778-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44778-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44778-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44778-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44778-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44778-114">See Also</span></span>  
    
 

---
title: "ICorDebugCode::IsIL 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.IsIL
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 07b0490e322c70763a37b86fbb02e2f8b99bd768
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="b04f7-102">ICorDebugCode::IsIL 方法</span><span class="sxs-lookup"><span data-stu-id="b04f7-102">ICorDebugCode::IsIL Method</span></span>
<span data-ttu-id="b04f7-103">取得值，指出是否此"ICorDebugCode 」 表示已編譯的 Microsoft 中繼語言 (MSIL) 中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b04f7-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b04f7-104">語法</span><span class="sxs-lookup"><span data-stu-id="b04f7-104">Syntax</span></span>  
  
```  
HRESULT IsIL (  
    [out] BOOL       *pbIL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b04f7-105">參數</span><span class="sxs-lookup"><span data-stu-id="b04f7-105">Parameters</span></span>  
 `pbIL`  
 <span data-ttu-id="b04f7-106">[out]`true`如果這個`ICorDebugCode`代表已編譯的 MSIL 中; 否則程式碼`false`。</span><span class="sxs-lookup"><span data-stu-id="b04f7-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b04f7-107">需求</span><span class="sxs-lookup"><span data-stu-id="b04f7-107">Requirements</span></span>  
 <span data-ttu-id="b04f7-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b04f7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b04f7-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b04f7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b04f7-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b04f7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b04f7-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b04f7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04f7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b04f7-112">See Also</span></span>  
 

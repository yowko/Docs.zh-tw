---
title: "ICorDebugProcess2::GetVersion 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.GetVersion
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 nterface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 84db785d47f97fe058b8a66070bcf4757fa11517
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="c42fa-102">ICorDebugProcess2::GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="c42fa-102">ICorDebugProcess2::GetVersion Method</span></span>
<span data-ttu-id="c42fa-103">取得 common language runtime (CLR) 執行此程序中的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="c42fa-103">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c42fa-104">語法</span><span class="sxs-lookup"><span data-stu-id="c42fa-104">Syntax</span></span>  
  
```  
HRESULT GetVersion (  
    [out] COR_VERSION     *version  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c42fa-105">參數</span><span class="sxs-lookup"><span data-stu-id="c42fa-105">Parameters</span></span>  
 `version`  
 <span data-ttu-id="c42fa-106">[out]儲存的執行階段的版本號碼 COR_VERSION 結構的指標。</span><span class="sxs-lookup"><span data-stu-id="c42fa-106">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c42fa-107">備註</span><span class="sxs-lookup"><span data-stu-id="c42fa-107">Remarks</span></span>  
 <span data-ttu-id="c42fa-108">`GetVersion`如果沒有執行階段載入處理序中，方法會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c42fa-108">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c42fa-109">需求</span><span class="sxs-lookup"><span data-stu-id="c42fa-109">Requirements</span></span>  
 <span data-ttu-id="c42fa-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c42fa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c42fa-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c42fa-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c42fa-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c42fa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c42fa-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c42fa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

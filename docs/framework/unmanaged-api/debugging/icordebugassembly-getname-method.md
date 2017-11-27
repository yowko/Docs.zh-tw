---
title: "ICorDebugAssembly::GetName 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d54139f8d7562f7f1ceb6e704731cd890a5f99df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="f07d0-102">ICorDebugAssembly::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="f07d0-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="f07d0-103">取得組件的名稱這`ICorDebugAssembly`執行個體所表示。</span><span class="sxs-lookup"><span data-stu-id="f07d0-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f07d0-104">語法</span><span class="sxs-lookup"><span data-stu-id="f07d0-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f07d0-105">參數</span><span class="sxs-lookup"><span data-stu-id="f07d0-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f07d0-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="f07d0-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f07d0-107">[out]指定名稱的實際長度的整數指標。</span><span class="sxs-lookup"><span data-stu-id="f07d0-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="f07d0-108">[out]陣列，其中儲存的名稱。</span><span class="sxs-lookup"><span data-stu-id="f07d0-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f07d0-109">備註</span><span class="sxs-lookup"><span data-stu-id="f07d0-109">Remarks</span></span>  
 <span data-ttu-id="f07d0-110">`GetName`方法會傳回組件的完整路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f07d0-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f07d0-111">需求</span><span class="sxs-lookup"><span data-stu-id="f07d0-111">Requirements</span></span>  
 <span data-ttu-id="f07d0-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f07d0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f07d0-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f07d0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f07d0-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f07d0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f07d0-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f07d0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

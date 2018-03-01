---
title: "ISymUnmanagedSourceServerModule::GetSourceServerData 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f75ffbe3980a6c7587912a1cf099ef87888132a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="9106c-102">ISymUnmanagedSourceServerModule::GetSourceServerData 方法</span><span class="sxs-lookup"><span data-stu-id="9106c-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="9106c-103">傳回模組的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="9106c-103">Returns the source server data for the module.</span></span> <span data-ttu-id="9106c-104">呼叫端必須釋放資源，使用`CoTaskMemFree`。</span><span class="sxs-lookup"><span data-stu-id="9106c-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9106c-105">語法</span><span class="sxs-lookup"><span data-stu-id="9106c-105">Syntax</span></span>  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9106c-106">參數</span><span class="sxs-lookup"><span data-stu-id="9106c-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="9106c-107">[out]指標`ULONG32`接收大小，以位元組為單位的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="9106c-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="9106c-108">[out]所傳回的指標`pDataByteCount`值。</span><span class="sxs-lookup"><span data-stu-id="9106c-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9106c-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="9106c-109">Return Value</span></span>  
 <span data-ttu-id="9106c-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="9106c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9106c-111">需求</span><span class="sxs-lookup"><span data-stu-id="9106c-111">Requirements</span></span>  
 <span data-ttu-id="9106c-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9106c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9106c-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="9106c-113">See Also</span></span>  
 [<span data-ttu-id="9106c-114">ISymUnmanagedSourceServerModule 介面</span><span class="sxs-lookup"><span data-stu-id="9106c-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)

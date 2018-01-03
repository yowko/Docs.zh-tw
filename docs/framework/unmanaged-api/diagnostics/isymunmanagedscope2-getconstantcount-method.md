---
title: "ISymUnmanagedScope2::GetConstantCount 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope2.GetConstantCount
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23584f4b29469976f62308f9ff7fe56c0a3875be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="8f000-102">ISymUnmanagedScope2::GetConstantCount 方法</span><span class="sxs-lookup"><span data-stu-id="8f000-102">ISymUnmanagedScope2::GetConstantCount Method</span></span>
<span data-ttu-id="8f000-103">取得此範圍內定義的常數的計數。</span><span class="sxs-lookup"><span data-stu-id="8f000-103">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f000-104">語法</span><span class="sxs-lookup"><span data-stu-id="8f000-104">Syntax</span></span>  
  
```  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f000-105">參數</span><span class="sxs-lookup"><span data-stu-id="8f000-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="8f000-106">[out]指標`ULONG32`接收以字元為單位，才能包含常數緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="8f000-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f000-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="8f000-107">Return Value</span></span>  
 <span data-ttu-id="8f000-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="8f000-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f000-109">需求</span><span class="sxs-lookup"><span data-stu-id="8f000-109">Requirements</span></span>  
 <span data-ttu-id="8f000-110">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8f000-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f000-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="8f000-111">See Also</span></span>  
 [<span data-ttu-id="8f000-112">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="8f000-112">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)

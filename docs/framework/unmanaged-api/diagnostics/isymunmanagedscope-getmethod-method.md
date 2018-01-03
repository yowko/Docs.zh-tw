---
title: "ISymUnmanagedScope::GetMethod 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4756ff1f373f09a96daa64c1fb01875274a6d0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="7e6c8-102">ISymUnmanagedScope::GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="7e6c8-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="7e6c8-103">取得包含此範圍的方法。</span><span class="sxs-lookup"><span data-stu-id="7e6c8-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e6c8-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e6c8-104">Syntax</span></span>  
  
```  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e6c8-105">參數</span><span class="sxs-lookup"><span data-stu-id="7e6c8-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="7e6c8-106">[out]所傳回的指標[ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="7e6c8-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e6c8-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="7e6c8-107">Return Value</span></span>  
 <span data-ttu-id="7e6c8-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="7e6c8-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e6c8-109">需求</span><span class="sxs-lookup"><span data-stu-id="7e6c8-109">Requirements</span></span>  
 <span data-ttu-id="7e6c8-110">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7e6c8-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e6c8-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="7e6c8-111">See Also</span></span>  
 [<span data-ttu-id="7e6c8-112">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="7e6c8-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)

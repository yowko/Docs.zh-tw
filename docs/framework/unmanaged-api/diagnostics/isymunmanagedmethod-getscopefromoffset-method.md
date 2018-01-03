---
title: "ISymUnmanagedMethod::GetScopeFromOffset 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetScopeFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 890fd702bc2edb5714dc9c91a618c6420a11a27a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="cc76e-102">ISymUnmanagedMethod::GetScopeFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="cc76e-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="cc76e-103">取得圍住儲存指定的位移這個方法內的最封入語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="cc76e-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="cc76e-104">這可以用來啟動本機變數搜尋。</span><span class="sxs-lookup"><span data-stu-id="cc76e-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc76e-105">語法</span><span class="sxs-lookup"><span data-stu-id="cc76e-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc76e-106">參數</span><span class="sxs-lookup"><span data-stu-id="cc76e-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="cc76e-107">[in]A`ULONG`包含位移。</span><span class="sxs-lookup"><span data-stu-id="cc76e-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="cc76e-108">[out]設定的指標所傳回[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="cc76e-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc76e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="cc76e-109">Return Value</span></span>  
 <span data-ttu-id="cc76e-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="cc76e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc76e-111">需求</span><span class="sxs-lookup"><span data-stu-id="cc76e-111">Requirements</span></span>  
 <span data-ttu-id="cc76e-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cc76e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc76e-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="cc76e-113">See Also</span></span>  
 [<span data-ttu-id="cc76e-114">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="cc76e-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

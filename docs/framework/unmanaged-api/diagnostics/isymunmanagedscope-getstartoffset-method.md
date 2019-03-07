---
title: ISymUnmanagedScope::GetStartOffset 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 189e72e513a06bfa545007fc9a8612a61314a520
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492657"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="41532-102">ISymUnmanagedScope::GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="41532-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="41532-103">取得此範圍的開始位移。</span><span class="sxs-lookup"><span data-stu-id="41532-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41532-104">語法</span><span class="sxs-lookup"><span data-stu-id="41532-104">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41532-105">參數</span><span class="sxs-lookup"><span data-stu-id="41532-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="41532-106">[out]指標`ULONG32`，其中包含的起始位移。</span><span class="sxs-lookup"><span data-stu-id="41532-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41532-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="41532-107">Return Value</span></span>  
 <span data-ttu-id="41532-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="41532-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41532-109">需求</span><span class="sxs-lookup"><span data-stu-id="41532-109">Requirements</span></span>  
 <span data-ttu-id="41532-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="41532-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41532-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41532-111">See also</span></span>
- [<span data-ttu-id="41532-112">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="41532-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="41532-113">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="41532-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)

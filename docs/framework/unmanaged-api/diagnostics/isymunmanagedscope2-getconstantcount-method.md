---
title: ISymUnmanagedScope2::GetConstantCount 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d1dfc9ead6256ae700d5e619da4fae5745bdd759
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485147"
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="fe59c-102">ISymUnmanagedScope2::GetConstantCount 方法</span><span class="sxs-lookup"><span data-stu-id="fe59c-102">ISymUnmanagedScope2::GetConstantCount Method</span></span>
<span data-ttu-id="fe59c-103">取得此範圍內所定義的計數。</span><span class="sxs-lookup"><span data-stu-id="fe59c-103">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe59c-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe59c-104">Syntax</span></span>  
  
```  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe59c-105">參數</span><span class="sxs-lookup"><span data-stu-id="fe59c-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="fe59c-106">[out]指標`ULONG32`接收大小，以字元為單位，以包含常數所需要的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="fe59c-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe59c-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="fe59c-107">Return Value</span></span>  
 <span data-ttu-id="fe59c-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="fe59c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe59c-109">需求</span><span class="sxs-lookup"><span data-stu-id="fe59c-109">Requirements</span></span>  
 <span data-ttu-id="fe59c-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fe59c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe59c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe59c-111">See also</span></span>
- [<span data-ttu-id="fe59c-112">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="fe59c-112">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)

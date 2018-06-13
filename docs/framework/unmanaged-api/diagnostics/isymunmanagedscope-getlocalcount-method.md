---
title: ISymUnmanagedScope::GetLocalCount 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2f8dde609f83a0bbf040ce0e8a4f164259e8584a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427923"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="d7c6f-102">ISymUnmanagedScope::GetLocalCount 方法</span><span class="sxs-lookup"><span data-stu-id="d7c6f-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="d7c6f-103">取得此範圍內定義的本機變數的計數。</span><span class="sxs-lookup"><span data-stu-id="d7c6f-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7c6f-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7c6f-104">Syntax</span></span>  
  
```  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7c6f-105">參數</span><span class="sxs-lookup"><span data-stu-id="d7c6f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="d7c6f-106">[out]指標`ULONG32`接收的本機變數的計數。</span><span class="sxs-lookup"><span data-stu-id="d7c6f-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7c6f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d7c6f-107">Return Value</span></span>  
 <span data-ttu-id="d7c6f-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="d7c6f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7c6f-109">需求</span><span class="sxs-lookup"><span data-stu-id="d7c6f-109">Requirements</span></span>  
 <span data-ttu-id="d7c6f-110">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d7c6f-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7c6f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7c6f-111">See Also</span></span>  
 [<span data-ttu-id="d7c6f-112">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="d7c6f-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)

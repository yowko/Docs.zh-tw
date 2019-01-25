---
title: ISymUnmanagedScope::GetEndOffset 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 739398d8c20f58d8b5e458e2de4cbb6f56c50fd8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624146"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="ea491-102">ISymUnmanagedScope::GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="ea491-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="ea491-103">取得此範圍的結束位移。</span><span class="sxs-lookup"><span data-stu-id="ea491-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea491-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea491-104">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea491-105">參數</span><span class="sxs-lookup"><span data-stu-id="ea491-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ea491-106">[out]指標`ULONG32`接收的結束位移。</span><span class="sxs-lookup"><span data-stu-id="ea491-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea491-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ea491-107">Return Value</span></span>  
 <span data-ttu-id="ea491-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="ea491-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea491-109">需求</span><span class="sxs-lookup"><span data-stu-id="ea491-109">Requirements</span></span>  
 <span data-ttu-id="ea491-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ea491-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea491-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea491-111">See also</span></span>
- [<span data-ttu-id="ea491-112">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="ea491-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="ea491-113">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="ea491-113">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)

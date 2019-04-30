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
ms.openlocfilehash: e28a351b6d47d14f171b9e760b2fa2c6755e3f8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986177"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="4710e-102">ISymUnmanagedScope::GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="4710e-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="4710e-103">取得此範圍的結束位移。</span><span class="sxs-lookup"><span data-stu-id="4710e-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4710e-104">語法</span><span class="sxs-lookup"><span data-stu-id="4710e-104">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4710e-105">參數</span><span class="sxs-lookup"><span data-stu-id="4710e-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="4710e-106">[out]指標`ULONG32`接收的結束位移。</span><span class="sxs-lookup"><span data-stu-id="4710e-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4710e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="4710e-107">Return Value</span></span>  
 <span data-ttu-id="4710e-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="4710e-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4710e-109">需求</span><span class="sxs-lookup"><span data-stu-id="4710e-109">Requirements</span></span>  
 <span data-ttu-id="4710e-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4710e-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4710e-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4710e-111">See also</span></span>

- [<span data-ttu-id="4710e-112">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="4710e-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="4710e-113">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="4710e-113">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)

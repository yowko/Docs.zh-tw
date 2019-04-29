---
title: ISymUnmanagedMethod::GetRootScope 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRootScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7c77be0dde950693d3943e41c392dcdcd9bc995e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939603"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="42c34-102">ISymUnmanagedMethod::GetRootScope 方法</span><span class="sxs-lookup"><span data-stu-id="42c34-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="42c34-103">取得這個方法內的根語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="42c34-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="42c34-104">這個範圍會封入整個方法。</span><span class="sxs-lookup"><span data-stu-id="42c34-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42c34-105">語法</span><span class="sxs-lookup"><span data-stu-id="42c34-105">Syntax</span></span>  
  
```  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42c34-106">參數</span><span class="sxs-lookup"><span data-stu-id="42c34-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="42c34-107">[out]設定指標所傳回[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="42c34-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42c34-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="42c34-108">Return Value</span></span>  
 <span data-ttu-id="42c34-109">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="42c34-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42c34-110">需求</span><span class="sxs-lookup"><span data-stu-id="42c34-110">Requirements</span></span>  
 <span data-ttu-id="42c34-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="42c34-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42c34-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42c34-112">See also</span></span>

- [<span data-ttu-id="42c34-113">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="42c34-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

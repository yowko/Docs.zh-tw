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
ms.openlocfilehash: 417ce67d807fddd3b99ceff4b05f1524db3044e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430524"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="48ba7-102">ISymUnmanagedMethod::GetRootScope 方法</span><span class="sxs-lookup"><span data-stu-id="48ba7-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="48ba7-103">取得這個方法內的根語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="48ba7-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="48ba7-104">這個範圍會封入整個方法。</span><span class="sxs-lookup"><span data-stu-id="48ba7-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48ba7-105">語法</span><span class="sxs-lookup"><span data-stu-id="48ba7-105">Syntax</span></span>  
  
```  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48ba7-106">參數</span><span class="sxs-lookup"><span data-stu-id="48ba7-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="48ba7-107">[out]設定的指標所傳回[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="48ba7-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48ba7-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="48ba7-108">Return Value</span></span>  
 <span data-ttu-id="48ba7-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="48ba7-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48ba7-110">需求</span><span class="sxs-lookup"><span data-stu-id="48ba7-110">Requirements</span></span>  
 <span data-ttu-id="48ba7-111">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="48ba7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48ba7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48ba7-112">See Also</span></span>  
 [<span data-ttu-id="48ba7-113">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="48ba7-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

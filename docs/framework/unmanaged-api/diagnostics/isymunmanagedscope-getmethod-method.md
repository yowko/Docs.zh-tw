---
title: ISymUnmanagedScope::GetMethod 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ebef54baf4e560b364845a521e4b4444ed359395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426116"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="e161b-102">ISymUnmanagedScope::GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="e161b-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="e161b-103">取得包含此範圍的方法。</span><span class="sxs-lookup"><span data-stu-id="e161b-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e161b-104">語法</span><span class="sxs-lookup"><span data-stu-id="e161b-104">Syntax</span></span>  
  
```  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e161b-105">參數</span><span class="sxs-lookup"><span data-stu-id="e161b-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="e161b-106">[out]所傳回的指標[ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="e161b-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e161b-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="e161b-107">Return Value</span></span>  
 <span data-ttu-id="e161b-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="e161b-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e161b-109">需求</span><span class="sxs-lookup"><span data-stu-id="e161b-109">Requirements</span></span>  
 <span data-ttu-id="e161b-110">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e161b-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e161b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e161b-111">See Also</span></span>  
 [<span data-ttu-id="e161b-112">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="e161b-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)

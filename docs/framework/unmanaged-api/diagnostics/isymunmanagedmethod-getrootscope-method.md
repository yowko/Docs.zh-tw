---
title: "ISymUnmanagedMethod::GetRootScope 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetRootScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 82b03e6db75d69d1d36f0137922448bad165e6ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="232b1-102">ISymUnmanagedMethod::GetRootScope 方法</span><span class="sxs-lookup"><span data-stu-id="232b1-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="232b1-103">取得這個方法內的根語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="232b1-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="232b1-104">這個範圍會封入整個方法。</span><span class="sxs-lookup"><span data-stu-id="232b1-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="232b1-105">語法</span><span class="sxs-lookup"><span data-stu-id="232b1-105">Syntax</span></span>  
  
```  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="232b1-106">參數</span><span class="sxs-lookup"><span data-stu-id="232b1-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="232b1-107">[out]設定的指標所傳回[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="232b1-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="232b1-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="232b1-108">Return Value</span></span>  
 <span data-ttu-id="232b1-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="232b1-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="232b1-110">需求</span><span class="sxs-lookup"><span data-stu-id="232b1-110">Requirements</span></span>  
 <span data-ttu-id="232b1-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="232b1-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="232b1-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="232b1-112">See Also</span></span>  
 [<span data-ttu-id="232b1-113">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="232b1-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

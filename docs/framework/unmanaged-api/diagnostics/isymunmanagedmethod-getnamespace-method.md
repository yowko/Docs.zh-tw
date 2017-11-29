---
title: "ISymUnmanagedMethod::GetNamespace 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5aff1bcd98e67f381340ed81a187db591c0986be
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="f3700-102">ISymUnmanagedMethod::GetNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="f3700-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="f3700-103">取得在其中定義這個方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f3700-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3700-104">語法</span><span class="sxs-lookup"><span data-stu-id="f3700-104">Syntax</span></span>  
  
```  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3700-105">參數</span><span class="sxs-lookup"><span data-stu-id="f3700-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f3700-106">[out]設定的指標所傳回[ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="f3700-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3700-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f3700-107">Return Value</span></span>  
 <span data-ttu-id="f3700-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="f3700-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3700-109">需求</span><span class="sxs-lookup"><span data-stu-id="f3700-109">Requirements</span></span>  
 <span data-ttu-id="f3700-110">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f3700-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3700-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3700-111">See Also</span></span>  
 [<span data-ttu-id="f3700-112">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="f3700-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

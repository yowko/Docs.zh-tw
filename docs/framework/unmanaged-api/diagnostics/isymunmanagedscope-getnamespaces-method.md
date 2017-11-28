---
title: "ISymUnmanagedScope::GetNamespaces 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetNamespaces
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 641ce6c4587f9f23743a3c1b5a1aeb6fb77edde7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="4d7a7-102">ISymUnmanagedScope::GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="4d7a7-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="4d7a7-103">取得此範圍內使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="4d7a7-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d7a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="4d7a7-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d7a7-105">參數</span><span class="sxs-lookup"><span data-stu-id="4d7a7-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="4d7a7-106">[in] `namespaces` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="4d7a7-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="4d7a7-107">[out]指標`ULONG32`包含命名空間所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="4d7a7-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="4d7a7-108">[out]接收的命名空間的陣列。</span><span class="sxs-lookup"><span data-stu-id="4d7a7-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d7a7-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="4d7a7-109">Return Value</span></span>  
 <span data-ttu-id="4d7a7-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="4d7a7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d7a7-111">需求</span><span class="sxs-lookup"><span data-stu-id="4d7a7-111">Requirements</span></span>  
 <span data-ttu-id="4d7a7-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4d7a7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d7a7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d7a7-113">See Also</span></span>  
 [<span data-ttu-id="4d7a7-114">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="4d7a7-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)

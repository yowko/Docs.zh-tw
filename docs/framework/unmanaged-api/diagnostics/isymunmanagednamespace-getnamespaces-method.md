---
title: "ISymUnmanagedNamespace::GetNamespaces 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedNamespace.GetNamespaces
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ef84358443520aa0548ef2244c2537b7a593f9e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="04b64-102">ISymUnmanagedNamespace::GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="04b64-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="04b64-103">取得這個命名空間的子系。</span><span class="sxs-lookup"><span data-stu-id="04b64-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04b64-104">語法</span><span class="sxs-lookup"><span data-stu-id="04b64-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04b64-105">參數</span><span class="sxs-lookup"><span data-stu-id="04b64-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="04b64-106">[in]A`ULONG32`指出的大小`namespaces`陣列。</span><span class="sxs-lookup"><span data-stu-id="04b64-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="04b64-107">[out]指標`ULONG32`接收以字元為單位，包含命名空間所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="04b64-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="04b64-108">[out]包含命名空間緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="04b64-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04b64-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="04b64-109">Return Value</span></span>  
 <span data-ttu-id="04b64-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="04b64-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04b64-111">需求</span><span class="sxs-lookup"><span data-stu-id="04b64-111">Requirements</span></span>  
 <span data-ttu-id="04b64-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="04b64-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b64-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04b64-113">See Also</span></span>  
 [<span data-ttu-id="04b64-114">ISymUnmanagedNamespace 介面</span><span class="sxs-lookup"><span data-stu-id="04b64-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)

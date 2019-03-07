---
title: ISymUnmanagedNamespace::GetVariables 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 02fd9fd3a580946cda09f0c129f02cd1218a0c9a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471429"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="271a7-102">ISymUnmanagedNamespace::GetVariables 方法</span><span class="sxs-lookup"><span data-stu-id="271a7-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="271a7-103">傳回在此命名空間內的全域範圍中定義的所有變數。</span><span class="sxs-lookup"><span data-stu-id="271a7-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="271a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="271a7-104">Syntax</span></span>  
  
```  
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="271a7-105">參數</span><span class="sxs-lookup"><span data-stu-id="271a7-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="271a7-106">[in]A`ULONG32`表示的大小`pVars`陣列。</span><span class="sxs-lookup"><span data-stu-id="271a7-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="271a7-107">[out]指標`ULONG32`接收包含命名空間所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="271a7-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="271a7-108">[out]包含命名空間緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="271a7-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="271a7-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="271a7-109">Return Value</span></span>  
 <span data-ttu-id="271a7-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="271a7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="271a7-111">需求</span><span class="sxs-lookup"><span data-stu-id="271a7-111">Requirements</span></span>  
 <span data-ttu-id="271a7-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="271a7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="271a7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="271a7-113">See also</span></span>
- [<span data-ttu-id="271a7-114">ISymUnmanagedNamespace 介面</span><span class="sxs-lookup"><span data-stu-id="271a7-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)

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
ms.openlocfilehash: f554fa95f552285ad92d9f780a8d77f53e6890b6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707694"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="6db3f-102">ISymUnmanagedNamespace::GetVariables 方法</span><span class="sxs-lookup"><span data-stu-id="6db3f-102">ISymUnmanagedNamespace::GetVariables Method</span></span>

<span data-ttu-id="6db3f-103">傳回在此命名空間內的全域範圍中定義的所有變數。</span><span class="sxs-lookup"><span data-stu-id="6db3f-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6db3f-104">語法</span><span class="sxs-lookup"><span data-stu-id="6db3f-104">Syntax</span></span>  
  
```cpp
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6db3f-105">參數</span><span class="sxs-lookup"><span data-stu-id="6db3f-105">Parameters</span></span>  

 `cVars`  
 <span data-ttu-id="6db3f-106">在 `ULONG32` ，指出陣列的大小 `pVars` 。</span><span class="sxs-lookup"><span data-stu-id="6db3f-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="6db3f-107">擴展的指標 `ULONG32` ，會接收包含命名空間所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="6db3f-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="6db3f-108">擴展包含命名空間之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="6db3f-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6db3f-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6db3f-109">Return Value</span></span>  

 <span data-ttu-id="6db3f-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="6db3f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6db3f-111">需求</span><span class="sxs-lookup"><span data-stu-id="6db3f-111">Requirements</span></span>  

 <span data-ttu-id="6db3f-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="6db3f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6db3f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6db3f-113">See also</span></span>

- [<span data-ttu-id="6db3f-114">ISymUnmanagedNamespace 介面</span><span class="sxs-lookup"><span data-stu-id="6db3f-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)

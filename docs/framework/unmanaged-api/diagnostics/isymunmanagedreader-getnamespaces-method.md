---
title: ISymUnmanagedReader::GetNamespaces 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type:
- apiref
ms.openlocfilehash: c90cd0d21eca6875d3dae32e4ca80cf42e6140b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720590"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="e81d8-102">ISymUnmanagedReader::GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="e81d8-102">ISymUnmanagedReader::GetNamespaces Method</span></span>

<span data-ttu-id="e81d8-103">取得在此符號存放區內的全域範圍中定義的命名空間。</span><span class="sxs-lookup"><span data-stu-id="e81d8-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e81d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="e81d8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e81d8-105">參數</span><span class="sxs-lookup"><span data-stu-id="e81d8-105">Parameters</span></span>  

 `cNameSpaces`  
 <span data-ttu-id="e81d8-106">在命名空間陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="e81d8-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="e81d8-107">擴展變數的指標，此變數會接收命名空間清單的長度。</span><span class="sxs-lookup"><span data-stu-id="e81d8-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="e81d8-108">擴展接收命名空間清單之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="e81d8-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e81d8-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="e81d8-109">Return Value</span></span>  

 <span data-ttu-id="e81d8-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e81d8-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e81d8-111">需求</span><span class="sxs-lookup"><span data-stu-id="e81d8-111">Requirements</span></span>  

 <span data-ttu-id="e81d8-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="e81d8-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e81d8-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e81d8-113">See also</span></span>

- [<span data-ttu-id="e81d8-114">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="e81d8-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)

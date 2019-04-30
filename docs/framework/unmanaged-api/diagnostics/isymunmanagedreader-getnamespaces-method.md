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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 570532433483e9d0a08f4d685087c0736e135390
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993300"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="1f5fd-102">ISymUnmanagedReader::GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="1f5fd-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="1f5fd-103">取得在這個符號存放區內的全域範圍中定義的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f5fd-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f5fd-104">語法</span><span class="sxs-lookup"><span data-stu-id="1f5fd-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f5fd-105">參數</span><span class="sxs-lookup"><span data-stu-id="1f5fd-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="1f5fd-106">[in]命名空間陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="1f5fd-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="1f5fd-107">[out]接收的命名空間清單長度變數的指標。</span><span class="sxs-lookup"><span data-stu-id="1f5fd-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="1f5fd-108">[out]接收命名空間清單中的變數指標。</span><span class="sxs-lookup"><span data-stu-id="1f5fd-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f5fd-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="1f5fd-109">Return Value</span></span>  
 <span data-ttu-id="1f5fd-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="1f5fd-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f5fd-111">需求</span><span class="sxs-lookup"><span data-stu-id="1f5fd-111">Requirements</span></span>  
 <span data-ttu-id="1f5fd-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1f5fd-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f5fd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f5fd-113">See also</span></span>

- [<span data-ttu-id="1f5fd-114">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="1f5fd-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

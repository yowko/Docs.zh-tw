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
ms.openlocfilehash: 44f9284f0a89f0941940cf379c48b2b138149122
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614938"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="a8e50-102">ISymUnmanagedReader::GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="a8e50-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="a8e50-103">取得在這個符號存放區的全域範圍中定義的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a8e50-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8e50-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8e50-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8e50-105">參數</span><span class="sxs-lookup"><span data-stu-id="a8e50-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="a8e50-106">在命名空間陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="a8e50-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="a8e50-107">脫銷接收命名空間清單長度之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="a8e50-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="a8e50-108">脫銷接收命名空間清單之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="a8e50-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8e50-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="a8e50-109">Return Value</span></span>  
 <span data-ttu-id="a8e50-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="a8e50-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8e50-111">需求</span><span class="sxs-lookup"><span data-stu-id="a8e50-111">Requirements</span></span>  
 <span data-ttu-id="a8e50-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="a8e50-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8e50-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8e50-113">See also</span></span>

- [<span data-ttu-id="a8e50-114">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="a8e50-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)

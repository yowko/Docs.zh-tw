---
title: "ISymUnmanagedReader::GetNamespaces 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetNamespaces
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c4404977fab42fb46292440473cd30f6cb162d6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="a4c0e-102">ISymUnmanagedReader::GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="a4c0e-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="a4c0e-103">取得在這個符號存放區內的全域範圍定義的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a4c0e-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4c0e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a4c0e-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4c0e-105">參數</span><span class="sxs-lookup"><span data-stu-id="a4c0e-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="a4c0e-106">[in]命名空間陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="a4c0e-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="a4c0e-107">[out]接收的命名空間清單長度變數的指標。</span><span class="sxs-lookup"><span data-stu-id="a4c0e-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="a4c0e-108">[out]會接收命名空間變數的指標。</span><span class="sxs-lookup"><span data-stu-id="a4c0e-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4c0e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="a4c0e-109">Return Value</span></span>  
 <span data-ttu-id="a4c0e-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="a4c0e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4c0e-111">需求</span><span class="sxs-lookup"><span data-stu-id="a4c0e-111">Requirements</span></span>  
 <span data-ttu-id="a4c0e-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a4c0e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c0e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4c0e-113">See Also</span></span>  
 [<span data-ttu-id="a4c0e-114">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="a4c0e-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

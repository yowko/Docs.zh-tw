---
title: ISymUnmanagedReader::GetDocuments 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocuments
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 629f9a62364729984a7eec86090876c3eaebb881
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57464551"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="e4674-102">ISymUnmanagedReader::GetDocuments 方法</span><span class="sxs-lookup"><span data-stu-id="e4674-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="e4674-103">傳回定義在符號存放區中的所有文件的陣列。</span><span class="sxs-lookup"><span data-stu-id="e4674-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4674-104">語法</span><span class="sxs-lookup"><span data-stu-id="e4674-104">Syntax</span></span>  
  
```  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4674-105">參數</span><span class="sxs-lookup"><span data-stu-id="e4674-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="e4674-106">[in] `pDocs` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="e4674-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="e4674-107">[out]此變數會接收陣列長度指標。</span><span class="sxs-lookup"><span data-stu-id="e4674-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="e4674-108">[out]接收文件陣列變數的指標。</span><span class="sxs-lookup"><span data-stu-id="e4674-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4674-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="e4674-109">Return Value</span></span>  
 <span data-ttu-id="e4674-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="e4674-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4674-111">需求</span><span class="sxs-lookup"><span data-stu-id="e4674-111">Requirements</span></span>  
 <span data-ttu-id="e4674-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e4674-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4674-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4674-113">See also</span></span>
- [<span data-ttu-id="e4674-114">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="e4674-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

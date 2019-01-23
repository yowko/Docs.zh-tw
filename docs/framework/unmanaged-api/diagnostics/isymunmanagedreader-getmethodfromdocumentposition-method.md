---
title: ISymUnmanagedReader::GetMethodFromDocumentPosition 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ebb1a13848b1c1336287413cdd7246da748ec864
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503955"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="8092c-102">ISymUnmanagedReader::GetMethodFromDocumentPosition 方法</span><span class="sxs-lookup"><span data-stu-id="8092c-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="8092c-103">傳回包含文件中指定位置的中斷點的方法。</span><span class="sxs-lookup"><span data-stu-id="8092c-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8092c-104">語法</span><span class="sxs-lookup"><span data-stu-id="8092c-104">Syntax</span></span>  
  
```  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8092c-105">參數</span><span class="sxs-lookup"><span data-stu-id="8092c-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="8092c-106">[in]指定的文件。</span><span class="sxs-lookup"><span data-stu-id="8092c-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="8092c-107">[in]指定的文件行。</span><span class="sxs-lookup"><span data-stu-id="8092c-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="8092c-108">[in]指定的文件的資料行。</span><span class="sxs-lookup"><span data-stu-id="8092c-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="8092c-109">[out]位址指標[ISymUnmanagedMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)物件，表示包含中斷點的方法。</span><span class="sxs-lookup"><span data-stu-id="8092c-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8092c-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="8092c-110">Return Value</span></span>  
 <span data-ttu-id="8092c-111">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="8092c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8092c-112">需求</span><span class="sxs-lookup"><span data-stu-id="8092c-112">Requirements</span></span>  
 <span data-ttu-id="8092c-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8092c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8092c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8092c-114">See also</span></span>
- [<span data-ttu-id="8092c-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="8092c-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

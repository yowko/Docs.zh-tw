---
title: "ISymUnmanagedReader::GetMethodFromDocumentPosition 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fa9bfa324254a48d43c4c3df5ecebb91b3f0ae1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="27f36-102">ISymUnmanagedReader::GetMethodFromDocumentPosition 方法</span><span class="sxs-lookup"><span data-stu-id="27f36-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="27f36-103">傳回包含中斷點的文件中指定位置的方法。</span><span class="sxs-lookup"><span data-stu-id="27f36-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27f36-104">語法</span><span class="sxs-lookup"><span data-stu-id="27f36-104">Syntax</span></span>  
  
```  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27f36-105">參數</span><span class="sxs-lookup"><span data-stu-id="27f36-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="27f36-106">[in]指定的文件。</span><span class="sxs-lookup"><span data-stu-id="27f36-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="27f36-107">[in]指定的文件行。</span><span class="sxs-lookup"><span data-stu-id="27f36-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="27f36-108">[in]指定的文件的資料行。</span><span class="sxs-lookup"><span data-stu-id="27f36-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="27f36-109">[out]位址指標[ISymUnmanagedMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)物件，代表包含中斷點的方法。</span><span class="sxs-lookup"><span data-stu-id="27f36-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27f36-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="27f36-110">Return Value</span></span>  
 <span data-ttu-id="27f36-111">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="27f36-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27f36-112">需求</span><span class="sxs-lookup"><span data-stu-id="27f36-112">Requirements</span></span>  
 <span data-ttu-id="27f36-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="27f36-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f36-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="27f36-114">See Also</span></span>  
 [<span data-ttu-id="27f36-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="27f36-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

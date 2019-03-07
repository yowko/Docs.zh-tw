---
title: ISymUnmanagedWriter::OpenNamespace 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4cf0fbcbf6af53c6a7865e2a2cf7874ea44581e4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474614"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="d8d9e-102">ISymUnmanagedWriter::OpenNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="d8d9e-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="d8d9e-103">開啟新的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d8d9e-103">Opens a new namespace.</span></span> <span data-ttu-id="d8d9e-104">佔用命名空間的方法或變數在定義之前呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="d8d9e-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="d8d9e-105">可以是巢狀命名空間。</span><span class="sxs-lookup"><span data-stu-id="d8d9e-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8d9e-106">語法</span><span class="sxs-lookup"><span data-stu-id="d8d9e-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8d9e-107">參數</span><span class="sxs-lookup"><span data-stu-id="d8d9e-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d8d9e-108">[in]新的命名空間名稱指標。</span><span class="sxs-lookup"><span data-stu-id="d8d9e-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8d9e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="d8d9e-109">Return Value</span></span>  
 <span data-ttu-id="d8d9e-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8d9e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8d9e-111">需求</span><span class="sxs-lookup"><span data-stu-id="d8d9e-111">Requirements</span></span>  
 <span data-ttu-id="d8d9e-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d8d9e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8d9e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8d9e-113">See also</span></span>
- [<span data-ttu-id="d8d9e-114">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="d8d9e-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="d8d9e-115">CloseNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="d8d9e-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)

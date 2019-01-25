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
ms.openlocfilehash: 2a108ec27cc4f8ed9d9d3c9227bf6ab0815fa933
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739689"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="04dbf-102">ISymUnmanagedWriter::OpenNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="04dbf-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="04dbf-103">開啟新的命名空間。</span><span class="sxs-lookup"><span data-stu-id="04dbf-103">Opens a new namespace.</span></span> <span data-ttu-id="04dbf-104">佔用命名空間的方法或變數在定義之前呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="04dbf-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="04dbf-105">可以是巢狀命名空間。</span><span class="sxs-lookup"><span data-stu-id="04dbf-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04dbf-106">語法</span><span class="sxs-lookup"><span data-stu-id="04dbf-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04dbf-107">參數</span><span class="sxs-lookup"><span data-stu-id="04dbf-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="04dbf-108">[in]新的命名空間名稱指標。</span><span class="sxs-lookup"><span data-stu-id="04dbf-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04dbf-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="04dbf-109">Return Value</span></span>  
 <span data-ttu-id="04dbf-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="04dbf-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04dbf-111">需求</span><span class="sxs-lookup"><span data-stu-id="04dbf-111">Requirements</span></span>  
 <span data-ttu-id="04dbf-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="04dbf-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04dbf-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04dbf-113">See also</span></span>
- [<span data-ttu-id="04dbf-114">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="04dbf-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="04dbf-115">CloseNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="04dbf-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)

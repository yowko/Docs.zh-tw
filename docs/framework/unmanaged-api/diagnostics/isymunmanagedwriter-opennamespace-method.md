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
ms.openlocfilehash: 02f57fdbbc1ea9a391d9c58c7ab49af0ef02f001
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426951"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="78afb-102">ISymUnmanagedWriter::OpenNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="78afb-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="78afb-103">開啟新的命名空間。</span><span class="sxs-lookup"><span data-stu-id="78afb-103">Opens a new namespace.</span></span> <span data-ttu-id="78afb-104">定義所佔用的命名空間的方法或變數之前呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="78afb-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="78afb-105">可以是巢狀命名空間。</span><span class="sxs-lookup"><span data-stu-id="78afb-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78afb-106">語法</span><span class="sxs-lookup"><span data-stu-id="78afb-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78afb-107">參數</span><span class="sxs-lookup"><span data-stu-id="78afb-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="78afb-108">[in]新的命名空間名稱指標。</span><span class="sxs-lookup"><span data-stu-id="78afb-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78afb-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="78afb-109">Return Value</span></span>  
 <span data-ttu-id="78afb-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="78afb-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78afb-111">需求</span><span class="sxs-lookup"><span data-stu-id="78afb-111">Requirements</span></span>  
 <span data-ttu-id="78afb-112">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="78afb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78afb-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78afb-113">See Also</span></span>  
 [<span data-ttu-id="78afb-114">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="78afb-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="78afb-115">CloseNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="78afb-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)

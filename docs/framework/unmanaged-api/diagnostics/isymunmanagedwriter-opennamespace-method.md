---
title: "ISymUnmanagedWriter::OpenNamespace 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e3dffd9605bd238446156d7a32e8e668ddd80916
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="c56d1-102">ISymUnmanagedWriter::OpenNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="c56d1-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="c56d1-103">開啟新的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c56d1-103">Opens a new namespace.</span></span> <span data-ttu-id="c56d1-104">定義所佔用的命名空間的方法或變數之前呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="c56d1-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="c56d1-105">可以是巢狀命名空間。</span><span class="sxs-lookup"><span data-stu-id="c56d1-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c56d1-106">語法</span><span class="sxs-lookup"><span data-stu-id="c56d1-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c56d1-107">參數</span><span class="sxs-lookup"><span data-stu-id="c56d1-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="c56d1-108">[in]新的命名空間名稱指標。</span><span class="sxs-lookup"><span data-stu-id="c56d1-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c56d1-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="c56d1-109">Return Value</span></span>  
 <span data-ttu-id="c56d1-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="c56d1-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c56d1-111">需求</span><span class="sxs-lookup"><span data-stu-id="c56d1-111">Requirements</span></span>  
 <span data-ttu-id="c56d1-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c56d1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c56d1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c56d1-113">See Also</span></span>  
 [<span data-ttu-id="c56d1-114">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="c56d1-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="c56d1-115">CloseNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="c56d1-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)

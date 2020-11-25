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
ms.openlocfilehash: 2f64f9f4bde3119f9f089becec5a36d69ed43596
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730057"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="76ab8-102">ISymUnmanagedWriter::OpenNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="76ab8-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>

<span data-ttu-id="76ab8-103">開啟新的命名空間。</span><span class="sxs-lookup"><span data-stu-id="76ab8-103">Opens a new namespace.</span></span> <span data-ttu-id="76ab8-104">在定義佔用命名空間的方法或變數之前，請先呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="76ab8-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="76ab8-105">命名空間可以嵌套。</span><span class="sxs-lookup"><span data-stu-id="76ab8-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76ab8-106">語法</span><span class="sxs-lookup"><span data-stu-id="76ab8-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76ab8-107">參數</span><span class="sxs-lookup"><span data-stu-id="76ab8-107">Parameters</span></span>  

 `name`  
 <span data-ttu-id="76ab8-108">在新命名空間名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="76ab8-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76ab8-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="76ab8-109">Return Value</span></span>  

 <span data-ttu-id="76ab8-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="76ab8-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76ab8-111">需求</span><span class="sxs-lookup"><span data-stu-id="76ab8-111">Requirements</span></span>  

 <span data-ttu-id="76ab8-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="76ab8-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ab8-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76ab8-113">See also</span></span>

- [<span data-ttu-id="76ab8-114">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="76ab8-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="76ab8-115">CloseNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="76ab8-115">CloseNamespace Method</span></span>](isymunmanagedwriter-closenamespace-method.md)

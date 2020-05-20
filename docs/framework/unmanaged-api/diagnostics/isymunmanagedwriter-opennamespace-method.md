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
ms.openlocfilehash: ab248c6a624fbed1a6783383566be093c449ff97
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609881"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="89de4-102">ISymUnmanagedWriter::OpenNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="89de4-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="89de4-103">開啟新的命名空間。</span><span class="sxs-lookup"><span data-stu-id="89de4-103">Opens a new namespace.</span></span> <span data-ttu-id="89de4-104">在定義佔用命名空間的方法或變數之前，請先呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="89de4-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="89de4-105">命名空間可以嵌套。</span><span class="sxs-lookup"><span data-stu-id="89de4-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89de4-106">語法</span><span class="sxs-lookup"><span data-stu-id="89de4-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89de4-107">參數</span><span class="sxs-lookup"><span data-stu-id="89de4-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="89de4-108">在新命名空間名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="89de4-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89de4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="89de4-109">Return Value</span></span>  
 <span data-ttu-id="89de4-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="89de4-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89de4-111">需求</span><span class="sxs-lookup"><span data-stu-id="89de4-111">Requirements</span></span>  
 <span data-ttu-id="89de4-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="89de4-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89de4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89de4-113">See also</span></span>

- [<span data-ttu-id="89de4-114">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="89de4-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="89de4-115">CloseNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="89de4-115">CloseNamespace Method</span></span>](isymunmanagedwriter-closenamespace-method.md)

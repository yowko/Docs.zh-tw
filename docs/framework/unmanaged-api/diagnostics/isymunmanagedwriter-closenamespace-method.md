---
title: ISymUnmanagedWriter::CloseNamespace 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::CloseNamespace method [.NET Framework debugging]
- CloseNamespace method [.NET Framework debugging]
ms.assetid: 7f74d9c5-1377-4958-b842-6306d611cbd5
topic_type:
- apiref
ms.openlocfilehash: 13a433157e0c92653edf234f1f1f885270196ffd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686406"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="a447f-102">ISymUnmanagedWriter::CloseNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="a447f-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>

<span data-ttu-id="a447f-103">關閉最近開啟的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a447f-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a447f-104">語法</span><span class="sxs-lookup"><span data-stu-id="a447f-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a447f-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="a447f-105">Return Value</span></span>  

 <span data-ttu-id="a447f-106">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="a447f-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a447f-107">需求</span><span class="sxs-lookup"><span data-stu-id="a447f-107">Requirements</span></span>  

 <span data-ttu-id="a447f-108">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="a447f-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a447f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a447f-109">See also</span></span>

- [<span data-ttu-id="a447f-110">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="a447f-110">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="a447f-111">OpenNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="a447f-111">OpenNamespace Method</span></span>](isymunmanagedwriter-opennamespace-method.md)

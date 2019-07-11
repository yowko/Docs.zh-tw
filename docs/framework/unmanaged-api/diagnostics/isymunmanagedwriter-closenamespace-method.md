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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ed618847d398bb4dcccb8ecebabdc947390c874
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778170"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="5ab58-102">ISymUnmanagedWriter::CloseNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="5ab58-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="5ab58-103">關閉最近開啟的命名空間。</span><span class="sxs-lookup"><span data-stu-id="5ab58-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ab58-104">語法</span><span class="sxs-lookup"><span data-stu-id="5ab58-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5ab58-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="5ab58-105">Return Value</span></span>  
 <span data-ttu-id="5ab58-106">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="5ab58-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ab58-107">需求</span><span class="sxs-lookup"><span data-stu-id="5ab58-107">Requirements</span></span>  
 <span data-ttu-id="5ab58-108">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5ab58-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ab58-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ab58-109">See also</span></span>

- [<span data-ttu-id="5ab58-110">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="5ab58-110">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="5ab58-111">OpenNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="5ab58-111">OpenNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)

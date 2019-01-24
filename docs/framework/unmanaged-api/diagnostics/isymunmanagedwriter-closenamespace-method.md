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
ms.openlocfilehash: 4429d49a489871a8993d9f841d9c5e7e37a53b5e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689675"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="21bb3-102">ISymUnmanagedWriter::CloseNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="21bb3-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="21bb3-103">關閉最近開啟的命名空間。</span><span class="sxs-lookup"><span data-stu-id="21bb3-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21bb3-104">語法</span><span class="sxs-lookup"><span data-stu-id="21bb3-104">Syntax</span></span>  
  
```  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="21bb3-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="21bb3-105">Return Value</span></span>  
 <span data-ttu-id="21bb3-106">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="21bb3-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21bb3-107">需求</span><span class="sxs-lookup"><span data-stu-id="21bb3-107">Requirements</span></span>  
 <span data-ttu-id="21bb3-108">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="21bb3-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21bb3-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21bb3-109">See also</span></span>
- [<span data-ttu-id="21bb3-110">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="21bb3-110">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="21bb3-111">OpenNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="21bb3-111">OpenNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)

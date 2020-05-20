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
ms.openlocfilehash: 7a4ffc0c417ae839e5c97ffe6884bc3230a603b7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610102"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="41ecb-102">ISymUnmanagedWriter::CloseNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="41ecb-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="41ecb-103">關閉最近開啟的命名空間。</span><span class="sxs-lookup"><span data-stu-id="41ecb-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41ecb-104">語法</span><span class="sxs-lookup"><span data-stu-id="41ecb-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="41ecb-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="41ecb-105">Return Value</span></span>  
 <span data-ttu-id="41ecb-106">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="41ecb-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41ecb-107">需求</span><span class="sxs-lookup"><span data-stu-id="41ecb-107">Requirements</span></span>  
 <span data-ttu-id="41ecb-108">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="41ecb-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41ecb-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41ecb-109">See also</span></span>

- [<span data-ttu-id="41ecb-110">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="41ecb-110">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="41ecb-111">OpenNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="41ecb-111">OpenNamespace Method</span></span>](isymunmanagedwriter-opennamespace-method.md)

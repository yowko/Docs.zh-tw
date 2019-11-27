---
title: ISymUnmanagedWriter::Close 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
ms.openlocfilehash: cd601ac6041ca22d59d7467bafc7c1d87b21371f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428121"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="bd790-102">ISymUnmanagedWriter::Close 方法</span><span class="sxs-lookup"><span data-stu-id="bd790-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="bd790-103">將符號認可到符號存放區之後，關閉符號寫入器。</span><span class="sxs-lookup"><span data-stu-id="bd790-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd790-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd790-104">Syntax</span></span>  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bd790-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="bd790-105">Return Value</span></span>  
 <span data-ttu-id="bd790-106">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="bd790-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd790-107">備註</span><span class="sxs-lookup"><span data-stu-id="bd790-107">Remarks</span></span>  
 <span data-ttu-id="bd790-108">在此呼叫之後，符號寫入器會變成無效，以便進行進一步的更新。</span><span class="sxs-lookup"><span data-stu-id="bd790-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="bd790-109">若要關閉符號寫入器而不認可符號，請改用[ISymUnmanagedWriter：： Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="bd790-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd790-110">需求</span><span class="sxs-lookup"><span data-stu-id="bd790-110">Requirements</span></span>  
 <span data-ttu-id="bd790-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="bd790-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd790-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd790-112">See also</span></span>

- [<span data-ttu-id="bd790-113">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="bd790-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

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
ms.openlocfilehash: 0a7ecd475a8031fedb2c8474593b45045fcc6fb9
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610128"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="b9649-102">ISymUnmanagedWriter::Close 方法</span><span class="sxs-lookup"><span data-stu-id="b9649-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="b9649-103">將符號認可到符號存放區之後，關閉符號寫入器。</span><span class="sxs-lookup"><span data-stu-id="b9649-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9649-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9649-104">Syntax</span></span>  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b9649-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="b9649-105">Return Value</span></span>  
 <span data-ttu-id="b9649-106">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="b9649-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9649-107">備註</span><span class="sxs-lookup"><span data-stu-id="b9649-107">Remarks</span></span>  
 <span data-ttu-id="b9649-108">在此呼叫之後，符號寫入器會變成無效，以便進行進一步的更新。</span><span class="sxs-lookup"><span data-stu-id="b9649-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="b9649-109">若要關閉符號寫入器而不認可符號，請改用[ISymUnmanagedWriter：： Abort](isymunmanagedwriter-abort-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b9649-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9649-110">需求</span><span class="sxs-lookup"><span data-stu-id="b9649-110">Requirements</span></span>  
 <span data-ttu-id="b9649-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="b9649-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9649-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9649-112">See also</span></span>

- [<span data-ttu-id="b9649-113">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="b9649-113">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)

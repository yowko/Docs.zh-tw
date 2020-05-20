---
title: ISymUnmanagedReader::GetMethod 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedReader interface [.NET Framework debugging]
- ISymUnmanagedReader::GetMethod method [.NET Framework debugging]
ms.assetid: ae6cfb29-bc2c-4606-af86-1d32ebd31020
topic_type:
- apiref
ms.openlocfilehash: 864acb07797676c825afe62321b0d65e37938fa6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615003"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="d61b3-102">ISymUnmanagedReader::GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="d61b3-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="d61b3-103">取得符號讀取器方法，並指定方法 token。</span><span class="sxs-lookup"><span data-stu-id="d61b3-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d61b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="d61b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d61b3-105">參數</span><span class="sxs-lookup"><span data-stu-id="d61b3-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="d61b3-106">在方法 token。</span><span class="sxs-lookup"><span data-stu-id="d61b3-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d61b3-107">脫銷傳回之介面的指標。</span><span class="sxs-lookup"><span data-stu-id="d61b3-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d61b3-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="d61b3-108">Return Value</span></span>  
 <span data-ttu-id="d61b3-109">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d61b3-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d61b3-110">需求</span><span class="sxs-lookup"><span data-stu-id="d61b3-110">Requirements</span></span>  
 <span data-ttu-id="d61b3-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d61b3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d61b3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d61b3-112">See also</span></span>

- [<span data-ttu-id="d61b3-113">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="d61b3-113">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)

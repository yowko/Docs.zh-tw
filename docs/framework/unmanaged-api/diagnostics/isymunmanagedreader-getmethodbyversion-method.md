---
title: ISymUnmanagedReader::GetMethodByVersion 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
ms.openlocfilehash: 60fbccabd21fb8bee118689a524efa9031bb2124
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614990"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="212b0-102">ISymUnmanagedReader::GetMethodByVersion 方法</span><span class="sxs-lookup"><span data-stu-id="212b0-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="212b0-103">取得符號讀取器方法，並指定方法權杖和編輯和複製版本號碼。</span><span class="sxs-lookup"><span data-stu-id="212b0-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="212b0-104">版本號碼從1開始，且每次方法因編輯和複製作業而變更時，都會遞增。</span><span class="sxs-lookup"><span data-stu-id="212b0-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="212b0-105">語法</span><span class="sxs-lookup"><span data-stu-id="212b0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="212b0-106">參數</span><span class="sxs-lookup"><span data-stu-id="212b0-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="212b0-107">在方法 token。</span><span class="sxs-lookup"><span data-stu-id="212b0-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="212b0-108">在方法版本。</span><span class="sxs-lookup"><span data-stu-id="212b0-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="212b0-109">脫銷傳回之介面的指標。</span><span class="sxs-lookup"><span data-stu-id="212b0-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="212b0-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="212b0-110">Return Value</span></span>  
 <span data-ttu-id="212b0-111">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="212b0-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="212b0-112">需求</span><span class="sxs-lookup"><span data-stu-id="212b0-112">Requirements</span></span>  
 <span data-ttu-id="212b0-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="212b0-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="212b0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="212b0-114">See also</span></span>

- [<span data-ttu-id="212b0-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="212b0-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)

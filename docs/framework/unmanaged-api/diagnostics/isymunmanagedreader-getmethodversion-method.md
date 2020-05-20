---
title: ISymUnmanagedReader::GetMethodVersion 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
ms.openlocfilehash: 8ee4c1bffccb44d15fa53eb3d4d6c0fcdc3e7697
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614964"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="864e2-102">ISymUnmanagedReader::GetMethodVersion 方法</span><span class="sxs-lookup"><span data-stu-id="864e2-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="864e2-103">取得方法版本。</span><span class="sxs-lookup"><span data-stu-id="864e2-103">Gets the method version.</span></span> <span data-ttu-id="864e2-104">方法版本從1開始，並在每次重新編譯方法時遞增。</span><span class="sxs-lookup"><span data-stu-id="864e2-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="864e2-105">重新編譯可能不會變更方法。</span><span class="sxs-lookup"><span data-stu-id="864e2-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="864e2-106">語法</span><span class="sxs-lookup"><span data-stu-id="864e2-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="864e2-107">參數</span><span class="sxs-lookup"><span data-stu-id="864e2-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="864e2-108">在要為其取得版本的方法。</span><span class="sxs-lookup"><span data-stu-id="864e2-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="864e2-109">脫銷接收方法版本之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="864e2-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="864e2-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="864e2-110">Return Value</span></span>  
 <span data-ttu-id="864e2-111">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="864e2-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="864e2-112">需求</span><span class="sxs-lookup"><span data-stu-id="864e2-112">Requirements</span></span>  
 <span data-ttu-id="864e2-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="864e2-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="864e2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="864e2-114">See also</span></span>

- [<span data-ttu-id="864e2-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="864e2-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)

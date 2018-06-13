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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76d850363940ff53135fc66ec057ee67822fa40d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424660"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="11da1-102">ISymUnmanagedReader::GetMethodVersion 方法</span><span class="sxs-lookup"><span data-stu-id="11da1-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="11da1-103">取得方法的版本。</span><span class="sxs-lookup"><span data-stu-id="11da1-103">Gets the method version.</span></span> <span data-ttu-id="11da1-104">方法版本 1 開始，且會增加的每當重新編譯的方法。</span><span class="sxs-lookup"><span data-stu-id="11da1-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="11da1-105">重新編譯的方法可能會發生不需要任何變更。</span><span class="sxs-lookup"><span data-stu-id="11da1-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11da1-106">語法</span><span class="sxs-lookup"><span data-stu-id="11da1-106">Syntax</span></span>  
  
```  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11da1-107">參數</span><span class="sxs-lookup"><span data-stu-id="11da1-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="11da1-108">[in]要取得版本方法。</span><span class="sxs-lookup"><span data-stu-id="11da1-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="11da1-109">[out]變數會接收方法版本的指標。</span><span class="sxs-lookup"><span data-stu-id="11da1-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11da1-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="11da1-110">Return Value</span></span>  
 <span data-ttu-id="11da1-111">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="11da1-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11da1-112">需求</span><span class="sxs-lookup"><span data-stu-id="11da1-112">Requirements</span></span>  
 <span data-ttu-id="11da1-113">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="11da1-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11da1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11da1-114">See Also</span></span>  
 [<span data-ttu-id="11da1-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="11da1-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

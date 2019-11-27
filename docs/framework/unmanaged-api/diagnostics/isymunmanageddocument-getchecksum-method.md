---
title: ISymUnmanagedDocument::GetCheckSum 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
ms.openlocfilehash: 52e1fc20fbe1d8709c21cacde926cf8bebb49425
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449197"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="2b4b5-102">ISymUnmanagedDocument::GetCheckSum 方法</span><span class="sxs-lookup"><span data-stu-id="2b4b5-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="2b4b5-103">取得總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="2b4b5-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b4b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b4b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b4b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="2b4b5-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="2b4b5-106">在`data` 參數所提供的緩衝區長度</span><span class="sxs-lookup"><span data-stu-id="2b4b5-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="2b4b5-107">脫銷總和檢查碼的大小和長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="2b4b5-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="2b4b5-108">脫銷接收總和檢查碼的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2b4b5-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b4b5-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="2b4b5-109">Return Value</span></span>  
 <span data-ttu-id="2b4b5-110">如果方法成功，則 S_OK;否則，錯誤碼為。</span><span class="sxs-lookup"><span data-stu-id="2b4b5-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b4b5-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b4b5-111">See also</span></span>

- [<span data-ttu-id="2b4b5-112">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="2b4b5-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)

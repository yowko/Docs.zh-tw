---
title: ISymUnmanagedENCUpdate::InitializeForEnc 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.InitializeForEnc
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::InitializeForEnc
helpviewer_keywords:
- ISymUnmanagedENCUpdate::InitializeForEnc method [.NET Framework debugging]
- InitializeForEnc method [.NET Framework debugging]
ms.assetid: 796b2154-b53c-4d07-9e67-80fd6064725a
topic_type:
- apiref
ms.openlocfilehash: 96ac27bfd155eaf95b1880c2f4dee0e24330e446
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729040"
---
# <a name="isymunmanagedencupdateinitializeforenc-method"></a><span data-ttu-id="c5984-102">ISymUnmanagedENCUpdate::InitializeForEnc 方法</span><span class="sxs-lookup"><span data-stu-id="c5984-102">ISymUnmanagedENCUpdate::InitializeForEnc Method</span></span>

<span data-ttu-id="c5984-103">允許在第一次呼叫 [ISymUnmanagedENCUpdate：： UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) 方法之前，先計算方法界限。</span><span class="sxs-lookup"><span data-stu-id="c5984-103">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5984-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5984-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForEnc();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c5984-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="c5984-105">Return Value</span></span>  

 <span data-ttu-id="c5984-106">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c5984-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5984-107">需求</span><span class="sxs-lookup"><span data-stu-id="c5984-107">Requirements</span></span>  

 <span data-ttu-id="c5984-108">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="c5984-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5984-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5984-109">See also</span></span>

- [<span data-ttu-id="c5984-110">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="c5984-110">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)

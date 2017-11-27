---
title: "GetAssemblyRefHash 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetAssemblyRefHash
api_location: alink.dll
api_type: COM
f1_keywords: GetAssemblyRefHash
helpviewer_keywords: GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0a5987bac2a874b01a24732a7c78a926fad0e011
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="c57ab-102">GetAssemblyRefHash 方法</span><span class="sxs-lookup"><span data-stu-id="c57ab-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="c57ab-103">擷取指定的組件的雜湊 blob。</span><span class="sxs-lookup"><span data-stu-id="c57ab-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c57ab-104">語法</span><span class="sxs-lookup"><span data-stu-id="c57ab-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c57ab-105">參數</span><span class="sxs-lookup"><span data-stu-id="c57ab-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="c57ab-106">要雜湊會參考的組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="c57ab-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="c57ab-107">收到產生的雜湊 blob。</span><span class="sxs-lookup"><span data-stu-id="c57ab-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="c57ab-108">接收大小，以位元組為單位的雜湊 blob。</span><span class="sxs-lookup"><span data-stu-id="c57ab-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c57ab-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="c57ab-109">Return Value</span></span>  
 <span data-ttu-id="c57ab-110">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="c57ab-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c57ab-111">需求</span><span class="sxs-lookup"><span data-stu-id="c57ab-111">Requirements</span></span>  
 <span data-ttu-id="c57ab-112">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="c57ab-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c57ab-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c57ab-113">See Also</span></span>  
 [<span data-ttu-id="c57ab-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="c57ab-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c57ab-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="c57ab-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c57ab-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="c57ab-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

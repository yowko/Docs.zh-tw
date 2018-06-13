---
title: GetAssemblyRefHash 方法
ms.date: 03/30/2017
api_name:
- IALink.GetAssemblyRefHash
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetAssemblyRefHash
helpviewer_keywords:
- GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ccf60d067af356dda1870a2fb1dcca21966f16a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401482"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="1cbf8-102">GetAssemblyRefHash 方法</span><span class="sxs-lookup"><span data-stu-id="1cbf8-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="1cbf8-103">擷取指定的組件的雜湊 blob。</span><span class="sxs-lookup"><span data-stu-id="1cbf8-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cbf8-104">語法</span><span class="sxs-lookup"><span data-stu-id="1cbf8-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cbf8-105">參數</span><span class="sxs-lookup"><span data-stu-id="1cbf8-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="1cbf8-106">要雜湊會參考的組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="1cbf8-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="1cbf8-107">收到產生的雜湊 blob。</span><span class="sxs-lookup"><span data-stu-id="1cbf8-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="1cbf8-108">接收大小，以位元組為單位的雜湊 blob。</span><span class="sxs-lookup"><span data-stu-id="1cbf8-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1cbf8-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="1cbf8-109">Return Value</span></span>  
 <span data-ttu-id="1cbf8-110">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="1cbf8-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cbf8-111">需求</span><span class="sxs-lookup"><span data-stu-id="1cbf8-111">Requirements</span></span>  
 <span data-ttu-id="1cbf8-112">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="1cbf8-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cbf8-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cbf8-113">See Also</span></span>  
 [<span data-ttu-id="1cbf8-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="1cbf8-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="1cbf8-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="1cbf8-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="1cbf8-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="1cbf8-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

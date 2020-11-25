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
ms.openlocfilehash: af040c4a6c9b85930d2d9261f8587ba69eb204e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721474"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="8f5cf-102">GetAssemblyRefHash 方法</span><span class="sxs-lookup"><span data-stu-id="8f5cf-102">GetAssemblyRefHash Method</span></span>

<span data-ttu-id="8f5cf-103">抓取指定元件的雜湊 blob。</span><span class="sxs-lookup"><span data-stu-id="8f5cf-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f5cf-104">語法</span><span class="sxs-lookup"><span data-stu-id="8f5cf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f5cf-105">參數</span><span class="sxs-lookup"><span data-stu-id="8f5cf-105">Parameters</span></span>  

 `FileToken`  
 <span data-ttu-id="8f5cf-106">雜湊將參考的元件識別碼。</span><span class="sxs-lookup"><span data-stu-id="8f5cf-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="8f5cf-107">接收產生的雜湊 blob。</span><span class="sxs-lookup"><span data-stu-id="8f5cf-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="8f5cf-108">接收雜湊 blob 的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="8f5cf-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f5cf-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="8f5cf-109">Return Value</span></span>  

 <span data-ttu-id="8f5cf-110">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="8f5cf-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f5cf-111">需求</span><span class="sxs-lookup"><span data-stu-id="8f5cf-111">Requirements</span></span>  

 <span data-ttu-id="8f5cf-112">需要 alink。h</span><span class="sxs-lookup"><span data-stu-id="8f5cf-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f5cf-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f5cf-113">See also</span></span>

- [<span data-ttu-id="8f5cf-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="8f5cf-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8f5cf-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="8f5cf-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8f5cf-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="8f5cf-116">ALink API</span></span>](index.md)

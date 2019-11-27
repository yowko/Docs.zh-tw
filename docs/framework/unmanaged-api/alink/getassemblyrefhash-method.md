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
ms.openlocfilehash: c68f43ce2f79ee6e4ec44ce4b2f0dbfb1c1185fa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433882"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="320a2-102">GetAssemblyRefHash 方法</span><span class="sxs-lookup"><span data-stu-id="320a2-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="320a2-103">抓取指定元件的雜湊 blob。</span><span class="sxs-lookup"><span data-stu-id="320a2-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="320a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="320a2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="320a2-105">參數</span><span class="sxs-lookup"><span data-stu-id="320a2-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="320a2-106">雜湊將參考的元件識別碼。</span><span class="sxs-lookup"><span data-stu-id="320a2-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="320a2-107">接收產生的雜湊 blob。</span><span class="sxs-lookup"><span data-stu-id="320a2-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="320a2-108">接收雜湊 blob 的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="320a2-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="320a2-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="320a2-109">Return Value</span></span>  
 <span data-ttu-id="320a2-110">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="320a2-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="320a2-111">需求</span><span class="sxs-lookup"><span data-stu-id="320a2-111">Requirements</span></span>  
 <span data-ttu-id="320a2-112">需要 alink. h</span><span class="sxs-lookup"><span data-stu-id="320a2-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="320a2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="320a2-113">See also</span></span>

- [<span data-ttu-id="320a2-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="320a2-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="320a2-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="320a2-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="320a2-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="320a2-116">ALink API</span></span>](index.md)

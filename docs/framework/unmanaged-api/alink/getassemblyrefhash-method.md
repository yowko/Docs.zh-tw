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
ms.openlocfilehash: d19eebaa3aa0ebb6f9807f0cf277b7ed6183c148
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777202"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="acfef-102">GetAssemblyRefHash 方法</span><span class="sxs-lookup"><span data-stu-id="acfef-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="acfef-103">抓取指定元件的雜湊 blob。</span><span class="sxs-lookup"><span data-stu-id="acfef-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acfef-104">語法</span><span class="sxs-lookup"><span data-stu-id="acfef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="acfef-105">參數</span><span class="sxs-lookup"><span data-stu-id="acfef-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="acfef-106">雜湊將參考的元件識別碼。</span><span class="sxs-lookup"><span data-stu-id="acfef-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="acfef-107">接收產生的雜湊 blob。</span><span class="sxs-lookup"><span data-stu-id="acfef-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="acfef-108">接收雜湊 blob 的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="acfef-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="acfef-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="acfef-109">Return Value</span></span>  
 <span data-ttu-id="acfef-110">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="acfef-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acfef-111">需求</span><span class="sxs-lookup"><span data-stu-id="acfef-111">Requirements</span></span>  
 <span data-ttu-id="acfef-112">需要 alink. h</span><span class="sxs-lookup"><span data-stu-id="acfef-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acfef-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acfef-113">See also</span></span>

- [<span data-ttu-id="acfef-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="acfef-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="acfef-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="acfef-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="acfef-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="acfef-116">ALink API</span></span>](index.md)

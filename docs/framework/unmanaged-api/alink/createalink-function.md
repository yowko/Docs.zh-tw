---
title: CreateALink 函式
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
ms.openlocfilehash: 98c6ed4657dc69554a9fcca27145f65c621492f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683727"
---
# <a name="createalink-function"></a><span data-ttu-id="b4aff-102">CreateALink 函式</span><span class="sxs-lookup"><span data-stu-id="b4aff-102">CreateALink Function</span></span>

<span data-ttu-id="b4aff-103">建立元件連結器的實例，並將指標設定為指定的介面。</span><span class="sxs-lookup"><span data-stu-id="b4aff-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4aff-104">語法</span><span class="sxs-lookup"><span data-stu-id="b4aff-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4aff-105">參數</span><span class="sxs-lookup"><span data-stu-id="b4aff-105">Parameters</span></span>  
  
|<span data-ttu-id="b4aff-106">參數</span><span class="sxs-lookup"><span data-stu-id="b4aff-106">Parameter</span></span>|<span data-ttu-id="b4aff-107">描述</span><span class="sxs-lookup"><span data-stu-id="b4aff-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="b4aff-108">其中一個元件連結器介面的機構名稱。</span><span class="sxs-lookup"><span data-stu-id="b4aff-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="b4aff-109">成功完成時的位置會包含介面的指標 `riid` 。</span><span class="sxs-lookup"><span data-stu-id="b4aff-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b4aff-110">需求</span><span class="sxs-lookup"><span data-stu-id="b4aff-110">Requirements</span></span>  

 <span data-ttu-id="b4aff-111">連結 **庫**： alink.dll</span><span class="sxs-lookup"><span data-stu-id="b4aff-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4aff-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4aff-112">See also</span></span>

- [<span data-ttu-id="b4aff-113">Al.exe (元件連結器) </span><span class="sxs-lookup"><span data-stu-id="b4aff-113">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)

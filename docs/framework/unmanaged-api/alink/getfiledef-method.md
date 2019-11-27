---
title: GetFileDef 方法
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
ms.openlocfilehash: 6a561205602920123176bd421ca2ef1b601166c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426044"
---
# <a name="getfiledef-method"></a><span data-ttu-id="8f3bc-102">GetFileDef 方法</span><span class="sxs-lookup"><span data-stu-id="8f3bc-102">GetFileDef Method</span></span>
<span data-ttu-id="8f3bc-103">抓取中繼資料中使用的實際 FileDef token （而不是由 ALink 指派的 token）。</span><span class="sxs-lookup"><span data-stu-id="8f3bc-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f3bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="8f3bc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f3bc-105">參數</span><span class="sxs-lookup"><span data-stu-id="8f3bc-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8f3bc-106">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="8f3bc-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="8f3bc-107">從 AddFile 方法或 AddImport 方法抓取之已加入檔案的 Token。</span><span class="sxs-lookup"><span data-stu-id="8f3bc-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="8f3bc-108">接收 FileDef token。</span><span class="sxs-lookup"><span data-stu-id="8f3bc-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f3bc-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="8f3bc-109">Return Value</span></span>  
 <span data-ttu-id="8f3bc-110">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="8f3bc-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f3bc-111">需求</span><span class="sxs-lookup"><span data-stu-id="8f3bc-111">Requirements</span></span>  
 <span data-ttu-id="8f3bc-112">需要 alink. h</span><span class="sxs-lookup"><span data-stu-id="8f3bc-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f3bc-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f3bc-113">See also</span></span>

- [<span data-ttu-id="8f3bc-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="8f3bc-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8f3bc-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="8f3bc-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8f3bc-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="8f3bc-116">ALink API</span></span>](index.md)

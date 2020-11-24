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
ms.openlocfilehash: 42935813579d7f1d55a9f1daf9d8c6c1241f85be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684703"
---
# <a name="getfiledef-method"></a><span data-ttu-id="80ce6-102">GetFileDef 方法</span><span class="sxs-lookup"><span data-stu-id="80ce6-102">GetFileDef Method</span></span>

<span data-ttu-id="80ce6-103">抓取中繼資料 (中使用的實際 FileDef token，而不是由 ALink) 所指派的權杖。</span><span class="sxs-lookup"><span data-stu-id="80ce6-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80ce6-104">語法</span><span class="sxs-lookup"><span data-stu-id="80ce6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="80ce6-105">參數</span><span class="sxs-lookup"><span data-stu-id="80ce6-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="80ce6-106">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="80ce6-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="80ce6-107">從 AddFile 方法或 AddImport 方法取出的已新增檔案的標記。</span><span class="sxs-lookup"><span data-stu-id="80ce6-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="80ce6-108">接收 FileDef token。</span><span class="sxs-lookup"><span data-stu-id="80ce6-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80ce6-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="80ce6-109">Return Value</span></span>  

 <span data-ttu-id="80ce6-110">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="80ce6-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80ce6-111">需求</span><span class="sxs-lookup"><span data-stu-id="80ce6-111">Requirements</span></span>  

 <span data-ttu-id="80ce6-112">需要 alink。h</span><span class="sxs-lookup"><span data-stu-id="80ce6-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ce6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80ce6-113">See also</span></span>

- [<span data-ttu-id="80ce6-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="80ce6-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="80ce6-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="80ce6-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="80ce6-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="80ce6-116">ALink API</span></span>](index.md)

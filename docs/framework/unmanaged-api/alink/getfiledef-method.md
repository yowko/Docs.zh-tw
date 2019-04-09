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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9153c9b3735e265d59ba072f747c92434c95d9ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184492"
---
# <a name="getfiledef-method"></a><span data-ttu-id="755e7-102">GetFileDef 方法</span><span class="sxs-lookup"><span data-stu-id="755e7-102">GetFileDef Method</span></span>
<span data-ttu-id="755e7-103">擷取中繼資料 （而不是由 ALink 指派的權杖） 中所使用的實際 FileDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="755e7-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="755e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="755e7-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="755e7-105">參數</span><span class="sxs-lookup"><span data-stu-id="755e7-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="755e7-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="755e7-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="755e7-107">語彙基元的加入的檔案從 AddFile 方法或 AddImport 方法擷取。</span><span class="sxs-lookup"><span data-stu-id="755e7-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="755e7-108">接收 FileDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="755e7-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="755e7-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="755e7-109">Return Value</span></span>  
 <span data-ttu-id="755e7-110">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="755e7-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="755e7-111">需求</span><span class="sxs-lookup"><span data-stu-id="755e7-111">Requirements</span></span>  
 <span data-ttu-id="755e7-112">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="755e7-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="755e7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="755e7-113">See also</span></span>

- [<span data-ttu-id="755e7-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="755e7-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="755e7-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="755e7-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="755e7-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="755e7-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

---
title: "IMapToken::Map 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMapToken.Map
api_location: mscoree.dll
api_type: COM
f1_keywords: IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2e3a9701bab27764803442a3cd0c24c4e412deaf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="8eb19-102">IMapToken::Map 方法</span><span class="sxs-lookup"><span data-stu-id="8eb19-102">IMapToken::Map Method</span></span>
<span data-ttu-id="8eb19-103">將對應使用中繼資料簽章的組件之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="8eb19-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eb19-104">語法</span><span class="sxs-lookup"><span data-stu-id="8eb19-104">Syntax</span></span>  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8eb19-105">參數</span><span class="sxs-lookup"><span data-stu-id="8eb19-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="8eb19-106">[in]代表已匯入程式碼物件中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8eb19-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="8eb19-107">[in]表示發出程式碼物件中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8eb19-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8eb19-108">備註</span><span class="sxs-lookup"><span data-stu-id="8eb19-108">Remarks</span></span>  
 <span data-ttu-id="8eb19-109">發生語彙基元重新對應合併期間，原始語彙基元的範圍匯入 （來源） 中繼資料範圍並將新的語彙基元的範圍發出 （目標） 中繼資料範圍內。</span><span class="sxs-lookup"><span data-stu-id="8eb19-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eb19-110">需求</span><span class="sxs-lookup"><span data-stu-id="8eb19-110">Requirements</span></span>  
 <span data-ttu-id="8eb19-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8eb19-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eb19-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8eb19-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8eb19-113">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8eb19-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8eb19-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eb19-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb19-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8eb19-115">See Also</span></span>  
 [<span data-ttu-id="8eb19-116">IMapToken 介面</span><span class="sxs-lookup"><span data-stu-id="8eb19-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)

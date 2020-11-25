---
title: IMetaDataAssemblyImport::GetAssemblyRefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
ms.openlocfilehash: 25aefff46f7557f89f27d1eccab58c9c70d2d13e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722111"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="63e18-102">IMetaDataAssemblyImport::GetAssemblyRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="63e18-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>

<span data-ttu-id="63e18-103">取得具有指定中繼資料簽章之元件參考的屬性集。</span><span class="sxs-lookup"><span data-stu-id="63e18-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63e18-104">語法</span><span class="sxs-lookup"><span data-stu-id="63e18-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,
    [out] const void          **ppbPublicKeyOrToken,
    [out] ULONG                *pcbPublicKeyOrToken,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] ASSEMBLYMETADATA     *pMetaData,
    [out] const void           **ppbHashValue,
    [out] ULONG                *pcbHashValue,
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63e18-105">參數</span><span class="sxs-lookup"><span data-stu-id="63e18-105">Parameters</span></span>  

 `mdar`  
 <span data-ttu-id="63e18-106">在 `mdAssemblyRef` 元資料標記，代表要取得其屬性的元件參考。</span><span class="sxs-lookup"><span data-stu-id="63e18-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="63e18-107">擴展公開金鑰或元資料標記的指標。</span><span class="sxs-lookup"><span data-stu-id="63e18-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="63e18-108">擴展傳回的公開金鑰或 token 中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="63e18-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="63e18-109">擴展元件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="63e18-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="63e18-110">在的大小（以寬字元為單位） `szName` 。</span><span class="sxs-lookup"><span data-stu-id="63e18-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="63e18-111">擴展實際傳回的寬字元數的指標 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="63e18-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="63e18-112">擴展ASSEMBLYMETADATA 結構的指標，其中包含元件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="63e18-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="63e18-113">擴展雜湊值的指標。</span><span class="sxs-lookup"><span data-stu-id="63e18-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="63e18-114">`PublicKey`除非已設定[AssemblyRefFlags](assemblyrefflags-enumeration.md)列舉的 arfFullOriginator 旗標，否則這是所參考元件之屬性的雜湊（使用 sha-1 演算法）。</span><span class="sxs-lookup"><span data-stu-id="63e18-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="63e18-115">擴展傳回的雜湊值中的寬字元數。</span><span class="sxs-lookup"><span data-stu-id="63e18-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="63e18-116">擴展旗標的指標，描述套用至元件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="63e18-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="63e18-117">旗標值是一或多個 [CorAssemblyFlags](corassemblyflags-enumeration.md) 值的組合。</span><span class="sxs-lookup"><span data-stu-id="63e18-117">The flags value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63e18-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="63e18-118">Return Value</span></span>  

 <span data-ttu-id="63e18-119">如果成功，這個方法會傳回 S_OK;否則，它會傳回 Winerror.h. h 標頭檔中定義的其中一個錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="63e18-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63e18-120">需求</span><span class="sxs-lookup"><span data-stu-id="63e18-120">Requirements</span></span>  

 <span data-ttu-id="63e18-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="63e18-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63e18-122">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="63e18-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63e18-123">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="63e18-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="63e18-124">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63e18-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63e18-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63e18-125">See also</span></span>

- [<span data-ttu-id="63e18-126">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="63e18-126">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)

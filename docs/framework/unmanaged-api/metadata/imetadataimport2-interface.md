---
title: IMetaDataImport2 介面
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
ms.openlocfilehash: fe9e87618291218a41e52f80198ce9068c9c56e2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490390"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="a29f5-102">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="a29f5-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="a29f5-103">擴充[IMetaDataImport](imetadataimport-interface.md)介面，以提供使用泛型型別的功能。</span><span class="sxs-lookup"><span data-stu-id="a29f5-103">Extends the [IMetaDataImport](imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a29f5-104">方法</span><span class="sxs-lookup"><span data-stu-id="a29f5-104">Methods</span></span>  
  
|<span data-ttu-id="a29f5-105">方法</span><span class="sxs-lookup"><span data-stu-id="a29f5-105">Method</span></span>|<span data-ttu-id="a29f5-106">描述</span><span class="sxs-lookup"><span data-stu-id="a29f5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a29f5-107">EnumGenericParamConstraints 方法</span><span class="sxs-lookup"><span data-stu-id="a29f5-107">EnumGenericParamConstraints Method</span></span>](imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="a29f5-108">取得與指定標記所代表的泛型參數相關聯之泛型參數條件約束陣列的列舉值。</span><span class="sxs-lookup"><span data-stu-id="a29f5-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="a29f5-109">EnumGenericParams 方法</span><span class="sxs-lookup"><span data-stu-id="a29f5-109">EnumGenericParams Method</span></span>](imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="a29f5-110">取得與指定的 TypeDef 或 MethodDef token 相關聯之泛型參數標記陣列的列舉值。</span><span class="sxs-lookup"><span data-stu-id="a29f5-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="a29f5-111">EnumMethodSpecs 方法</span><span class="sxs-lookup"><span data-stu-id="a29f5-111">EnumMethodSpecs Method</span></span>](imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="a29f5-112">取得與指定的 MethodDef 或 MemberRef token 相關聯的 MethodSpec 標記陣列的列舉值。</span><span class="sxs-lookup"><span data-stu-id="a29f5-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="a29f5-113">GetGenericParamConstraintProps 方法</span><span class="sxs-lookup"><span data-stu-id="a29f5-113">GetGenericParamConstraintProps Method</span></span>](imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="a29f5-114">取得與指定之條件約束標記所表示的泛型參數條件約束相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a29f5-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="a29f5-115">GetGenericParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="a29f5-115">GetGenericParamProps Method</span></span>](imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="a29f5-116">取得與指定標記所表示的泛型參數相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a29f5-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="a29f5-117">GetMethodSpecProps 方法</span><span class="sxs-lookup"><span data-stu-id="a29f5-117">GetMethodSpecProps Method</span></span>](imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="a29f5-118">取得指定的 MethodSpec token 所參考之方法的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="a29f5-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="a29f5-119">GetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="a29f5-119">GetPEKind Method</span></span>](imetadataimport2-getpekind-method.md)|<span data-ttu-id="a29f5-120">取得值，識別可移植執行檔（PE）中的程式碼本質，通常是在目前中繼資料範圍中定義的 DLL 或 EXE 檔案</span><span class="sxs-lookup"><span data-stu-id="a29f5-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="a29f5-121">GetVersionString 方法</span><span class="sxs-lookup"><span data-stu-id="a29f5-121">GetVersionString Method</span></span>](imetadataimport2-getversionstring-method.md)|<span data-ttu-id="a29f5-122">取得用來建立元件之執行時間的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a29f5-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a29f5-123">規格需求</span><span class="sxs-lookup"><span data-stu-id="a29f5-123">Requirements</span></span>  
 <span data-ttu-id="a29f5-124">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a29f5-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a29f5-125">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="a29f5-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a29f5-126">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="a29f5-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a29f5-127">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a29f5-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a29f5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a29f5-128">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="a29f5-129">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="a29f5-129">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="a29f5-130">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="a29f5-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)

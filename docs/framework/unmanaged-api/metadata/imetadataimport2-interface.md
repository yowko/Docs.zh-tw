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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8c95249ec28b9018db42ec70443b30ae4f1409c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567213"
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2 介面
擴充[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)介面，以提供泛用型別所使用的功能。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumGenericParamConstraints 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|取得與指定的語彙基元所代表的泛型參數相關聯的泛型參數條件約束的陣列的列舉值。|  
|[EnumGenericParams 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|陣列的泛型參數指定的 TypeDef 或 MethodDef 相關聯的語彙基元的列舉值取得語彙基元。|  
|[EnumMethodSpecs 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|取得列舉值陣列的 methodspec Neobsahuje 相關聯的權杖與指定 MethodDef 或 MemberRef 語彙基元。|  
|[GetGenericParamConstraintProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|取得與指定的條件約束語彙基元所代表的泛型參數條件約束相關聯的中繼資料。|  
|[GetGenericParamProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|取得與指定的語彙基元所代表的泛型參數相關聯的中繼資料。|  
|[GetMethodSpecProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|取得指定 methodspec Neobsahuje 所參考之方法的中繼資料簽章語彙基元。|  
|[GetPEKind 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|取得值，識別性質的可攜式執行檔 (PE) 中的程式碼檔，通常是 DLL 或 EXE 檔案，在目前的中繼資料範圍中定義|  
|[GetVersionString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|取得執行階段用來建置組件的版本號碼。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Reflection.PortableExecutableKinds>
- [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

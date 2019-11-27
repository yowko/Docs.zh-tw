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
ms.openlocfilehash: 0fd7915ef46899bdce8312bc6e8a466167e26382
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429204"
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2 介面
擴充[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)介面，以提供使用泛型型別的功能。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumGenericParamConstraints 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|取得與指定標記所代表的泛型參數相關聯之泛型參數條件約束陣列的列舉值。|  
|[EnumGenericParams 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|取得與指定的 TypeDef 或 MethodDef token 相關聯之泛型參數標記陣列的列舉值。|  
|[EnumMethodSpecs 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|取得與指定的 MethodDef 或 MemberRef token 相關聯的 MethodSpec 標記陣列的列舉值。|  
|[GetGenericParamConstraintProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|取得與指定之條件約束標記所表示的泛型參數條件約束相關聯的中繼資料。|  
|[GetGenericParamProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|取得與指定標記所表示的泛型參數相關聯的中繼資料。|  
|[GetMethodSpecProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|取得指定的 MethodSpec token 所參考之方法的中繼資料簽章。|  
|[GetPEKind 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|取得值，識別可移植執行檔（PE）中的程式碼本質，通常是在目前中繼資料範圍中定義的 DLL 或 EXE 檔案|  
|[GetVersionString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|取得用來建立元件之執行時間的版本號碼。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Reflection.PortableExecutableKinds>
- [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

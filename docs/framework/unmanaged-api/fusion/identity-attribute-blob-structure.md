---
title: IDENTITY_ATTRIBUTE_BLOB 結構
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IDENTITY_ATTRIBUTE_BLOB
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE_BLOB
helpviewer_keywords:
- IDENTITY_ATTRIBUTE_BLOB structure [.NET Framework fusion]
ms.assetid: af14ae5f-d226-47dd-ba90-8fc6e6605d4d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58ee2764d2e2c4c4e21effa3e0c3551a2e145f40
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796499"
---
# <a name="identity_attribute_blob-structure"></a>IDENTITY_ATTRIBUTE_BLOB 結構
包含元件中單一屬性的相關資訊，並由三個`DWORD`組成。 每`DWORD`個都是[IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md)介面的方法所`CurrentIntoBuffer`產生之字元緩衝區的位移  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE_BLOB {  
    DWORD  ofsNamespace;  
    DWORD  ofsName;  
    DWORD  ofsValue;  
}   IDENTITY_ATTRIBUTE_BLOB;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`ofsNamespace`|字元緩衝區的第一個位移。 這個位移後面不接屬性的命名空間，而是一系列的 null 字元。 因此，不會使用它。|  
|`ofsName`|字元緩衝區的第二個位移。 這個位置會標示屬性名稱的開頭。|  
|`ofsValue`|字元緩衝區中的第三個位移。 這個位置會標示屬性值的開頭。|  
  
## <a name="sample"></a>範例  
 下列範例說明數個基本步驟，最後會產生一個已填入`IDENTITY_ATTRIBUTE_BLOB`的結構：  
  
1. 取得元件的[IReferenceIdentity](ireferenceidentity-interface.md) 。  
  
2. 呼叫`IReferenceIdentity::EnumAttributes`方法，並取得 [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md)。  
  
3. 建立字元緩衝區，並將它轉換成`IDENTITY_ATTRIBUTE_BLOB`結構。  
  
4. 呼叫介面`IEnumIDENTITY_ATTRIBUTE`的方法。 `CurrentIntoBuffer` 這個方法會將屬性`Namespace`、 `Name`和`Value`複製到字元緩衝區。 這些字串的三個位移會在`IDENTITY_ATTRIBUTE_BLOB`結構中變成可用。  
  
```cpp  
// EnumAssemblyAttributes.cpp : main project file.  
  
#include "stdafx.h"  
  
#include "fusion.h"  
#include "windows.h"  
#include "stdio.h"  
#include "mscoree.h"  
#include "isolation.h"  
  
typedef HRESULT (__stdcall *PFNGETREF)(LPCWSTR pwzFile, REFIID riid, IUnknown **ppUnk);  
typedef HRESULT (__stdcall *PFNGETAUTH)(IIdentityAuthority **ppIIdentityAuthority);  
  
PFNGETREF                   g_pfnGetAssemblyIdentityFromFile = NULL;  
PFNGETAUTH                  g_pfnGetIdentityAuthority = NULL;  
IUnknown                    *g_pUnk = NULL;  
  
bool Init()  
{  
    HRESULT     hr = S_OK;  
    DWORD       dwSize = 0;  
    bool        bRC = false;  
  
    hr = CorBindToRuntimeEx(NULL, L"wks", 0, CLSID_CorRuntimeHost,  
                           IID_ICorRuntimeHost, (void **)&g_pUnk);  
    if(FAILED(hr)) {  
        printf("Error: Failed to initialize CLR runtime! hr = 0x%0x\n",  
                hr);  
        goto Exit;  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetAssemblyIdentityFromFile",  
                         (VOID **)&g_pfnGetAssemblyIdentityFromFile);  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetIdentityAuthority",  
                                (VOID **)&g_pfnGetIdentityAuthority);  
    }  
  
    if (!g_pfnGetAssemblyIdentityFromFile ||   
        !g_pfnGetIdentityAuthority)  
    {  
        printf("Error: Cannot get required APIs from fusion.dll!\n");  
        goto Exit;  
    }  
  
    bRC = true;  
  
Exit:  
    return bRC;  
}  
  
void Shutdown()  
{  
    if(g_pUnk) {  
        g_pUnk->Release();  
        g_pUnk = NULL;  
    }  
}  
  
void Usage()  
{  
    printf("EnumAssemblyAttributes: A tool to enumerate the identity   
            attributes of a given assembly.\n\n");  
    printf("Usage: EnumAssemblyAttributes AssemblyFilePath\n");  
    printf("\n");  
}  
  
int _cdecl wmain(int argc, LPCWSTR argv[])  
{  
    int     iResult = 1;  
    IUnknown                    *pUnk  = NULL;  
    IReferenceIdentity          *pRef  = NULL;  
    HRESULT                     hr     = S_OK;     
    IEnumIDENTITY_ATTRIBUTE     *pEnum = NULL;  
    BYTE                        abData[1024];  
    DWORD                       cbAvailable;  
    DWORD                       cbUsed;  
    IDENTITY_ATTRIBUTE_BLOB     *pBlob;  
  
    if(argc != 2) {  
        Usage();  
        goto Exit;  
    }  
  
    if(!Init()) {  
        printf("Failure initializing EnumIdAttr.\n");  
        goto Exit;  
    }  
  
    hr = g_pfnGetAssemblyIdentityFromFile(argv[1],   
                            __uuidof(IReferenceIdentity), &pUnk);  
  
    if (FAILED(hr)) {  
        printf("GetAssemblyIdentityFromFile failed with hr = 0x%x",   
                hr);  
        goto Exit;  
    }  
  
    hr = pUnk->QueryInterface(__uuidof(IReferenceIdentity),   
                              (void**)&pRef);  
    if (FAILED(hr)) {  
        goto Exit;  
    }  
  
    hr = pRef->EnumAttributes(&pEnum);  
    if (FAILED(hr)) {  
        printf("IReferenceIdentity::EnumAttributes failed with hr =   
                0x%x", hr);  
        goto Exit;  
    }  
  
    pBlob = (IDENTITY_ATTRIBUTE_BLOB *)(abData);  
    while (1) {  
        cbAvailable = sizeof(abData);  
        hr = pEnum->CurrentIntoBuffer(cbAvailable, abData, &cbUsed);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer failed   
                    with hr = 0x%x", hr);  
            goto Exit;  
        }  
  
        if (! cbUsed) {  
            break;  
        }  
  
        LPWSTR pwzNameSpace = (LPWSTR)(abData + pBlob->ofsNamespace);  
        LPWSTR pwzName      = (LPWSTR)(abData + pBlob->ofsName);  
        LPWSTR pwzValue     = (LPWSTR)(abData + pBlob->ofsValue);  
        printf("%ws: %ws = %ws\n", pwzNameSpace, pwzName, pwzValue);  
  
        hr = pEnum->Skip(1);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::Skip failed with hr =   
                    0x%x", hr);  
            goto Exit;  
        }  
    }  
  
    iResult = 0;  
  
Exit:  
  
    Shutdown();  
  
    if (pUnk) {  
        pUnk->Release();  
    }  
  
    if (pRef) {  
        pRef->Release();  
    }  
  
    if (pEnum) {  
        pEnum->Release();  
    }  
  
    return iResult;  
}  
```  
  
### <a name="to-run-the-sample"></a>若要執行範例  
 C：\\> EnumAssemblyAttributes .exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll  
  
### <a name="sample-output"></a>範例輸出  
 文化特性 = 中性  
  
 名稱 = 系統  
  
 processorArchitecture = MSIL  
  
 PublicKeyToken = b77a5c561934e089  
  
 Version = 2.0.0。0  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IReferenceIdentity 介面](ireferenceidentity-interface.md)
- [IEnumIDENTITY_ATTRIBUTE 介面](ienumidentity-attribute-interface.md)
- [IDENTITY_ATTRIBUTE 結構](identity-attribute-structure.md)
- [融合結構](fusion-structures.md)
